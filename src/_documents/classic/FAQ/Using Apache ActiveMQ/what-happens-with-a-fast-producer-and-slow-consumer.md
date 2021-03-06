Apache ActiveMQ ™ -- What happens with a fast producer and slow consumer 

 [FAQ](/FAQ/index.md) > [Using Apache ActiveMQ](../../FAQ/using-apache-activemq.md) > [What happens with a fast producer and slow consumer](../../FAQ/Using Apache ActiveMQ/what-happens-with-a-fast-producer-and-slow-consumer.md)


It depends a little on the [QoS](../../FAQ/Terminology/qos.md) but in general we implement _flow control_ which means that when we have a very fast producer and a slow consumer, when we get to a high water mark of outstanding messages we will start to tell the producer to slow down (which occurs inside the JMS client automatically, no application code changes are required). The slow down messages will increase exponentially over time until things get back into balance again.

Flow control avoids unnecessary resouce exhaustion and is particularly useful in non-durable messaging modes to avoid running out of memory / disk on a node.

