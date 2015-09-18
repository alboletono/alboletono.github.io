---
layout: post
title: Distributed_Cache
categories: []
tags: []
published: True

---

Lots of intersting links about distributed cache:

- http://blog.xebia.fr/2009/08/26/les-caches-ces-armes-a-manipuler-avec-precaution/
- http://javalandscape.blogspot.in/2009/01/cachingcaching-algorithms-and-caching.html
- In-process caching vs Distributed Caching:
    - https://dzone.com/articles/process-caching-vs-distributed
- comparison with Memcached vs Redis vs Hazelcast http://blog.engineering.aol.com/2015/08/28/a-comparative-study-of-distributed-caches/
- history:
    - http://insights.wired.com/profiles/blogs/cache-data-grid-database#axzz3lu5l2nvW
- distributed cache vs Nosql
    - http://www.infoq.com/news/2011/11/distributed-cache-nosql-data-sto
- distributed caches died?
    - http://www.gridgain.com/distributed-caching-is-dead-long-live/
- video on data griding:
    - http://www.jboss.org/video/vimeo/32452279/
- BASE vs ACID:
    - http://www.johndcook.com/blog/2009/07/06/brewer-cap-theorem-base/
- OpenFHT:
    - http://vanillajava.blogspot.fr/2014/05/sharedhashmap-vs-redis.html

Technologies studied:


- Redis (NoSql that can be used as cache only)
    - http://www.codeproject.com/Articles/636730/Distributed-Caching-using-Redis
    - http://www.touilleur-express.fr/2013/04/03/redis/
- Infinispan (compatible memcached)
    - can be persisted
- JBoss Data Grid
    - based on JBoss application server and Infinispan
    - need a subscription?
- Java Caching System (JCS)
    - https://commons.apache.org/proper/commons-jcs
- Hazelcast (http://hazelcast.org/use-cases/caching/) --> free version but commercial features.





(see http://javalandscape.blogspot.fr/2009/03/intro-to-cachingcaching-algorithms-and.html)

Technologies ignored:

- Google Guava (not distributed, only in memory)
- Oracle Coherence
- ElastiCache solution amazone payante à base de Redis ou Memcached
    - https://aws.amazon.com/fr/elasticache/
- JBoss cache (TreeCache)(replaced by JBoss data grid) --> too old?
- EHCache (not distributed)
- Memcached in C but gave protocol that is wide spread
- Cassandra (nosql)
- VMWare Gemfire more big data oriented and not yet open sourced (but will be incubated by apache)
- Terracotta Enterprise Suite
    - commercial http://www.terracotta.org/products/enterprise-suite
- Cache4j (not distributed)
- WhirlyCache (not distributed)
- SwarmCache (no more activity)
- ZooKeeper + Helix (more general cluster)
- open HFT for very low latency

Mandatory criteria:
- distributed (few nodes) vs replicated (all nodes of the cluser)
- distributed lock (http://redis.io/topics/distlock)

Criteria:

- Core functionnalities
    - cache algos
    - langages
    - caching data type (POJO, HTTP, JSP, ORM)
    - POJO caching type: strings, objects, lists, sets, etc...
    - caching store (memory, disk, etc...)
    - object sharing same JVM
    - Invalidation implementations
    - security
    - standard (JSR 107)
    - transactional or not or both (may impact perf) --> ACID. JTA, XA
    - isolation level (READ_COMMITED, ISOLATION_LEVEL)
    - offheap
    - asynchroneous
    - mono/multi threaded
    - node autodiscovering (hotrod != memcached)
    - eviction != expiration
    - offheap/onheap
    - cluster communication protocol: JGroups




- Performance and reliability
    - read/write performance?
    - reliability (replication)

- Maintenance / scalability
    - ease of use, maintanability, extensibility
    - cloud readiness
    - horizontal scaling capability
    - cost?

ACID transactions, eviction policies, replication vs. partitioning, active backups
BASE not ACID

Read more: http://insights.wired.com/profiles/blogs/cache-data-grid-database#ixzz3luE8lCnd
Follow us: @Wiredinsights on Twitter | InnovationInsights on Facebook

Monitoring : jmx, jopr
protocols: api (jcache), hotrod, reset, memcached, websockets

Backoffice tool: standalone or online code or scripting

security: sasl, cachemanager, security realms, etc...

with replication or not
JTA compliant transaction 1SR 107 (temporary caching api)
JSR347 (for datagrid)

JPA compliancy (access datagrid like hibernate)

Hotrod smarter protocol

http://infinispan.org/features/

Three criteria:
- consistency (with transaction)
- availability (redundancy)
- partition tolerance: when two nodes can't talk to each other, but there are clients able to talk to either one or both of those nodes



Performance comparisons:
- https://commons.apache.org/proper/commons-jcs/JCSvsEHCache.html
- transaction breaks low latency?


    DÃ©couverte automatique des nÅ“uds sur le rÃ©seau (on dÃ©marre simplement un nouveau nÅ“ud avec une configuration identique).
    Synchronisation et rÃ©partition automatique des donnÃ©es sur chacun des nÅ“uds afin dâ€™assurer une haute disponibilitÃ©.
    RÃ©partition intelligente des donnÃ©es (Cache local) permettant de stocker les donnÃ©es au plus prÃªt de leur utilisation et Ã©vitant les accÃ¨s rÃ©seau.
    En cas de crash dâ€™un nÅ“ud les donnÃ©es quâ€™il contenait sont automatiquement rÃ©parties sur les nÅ“uds restant.
    La rÃ©partition des donnÃ©es est transparente pour le client (on accÃ¨de Ã  toutes les donnÃ©es Ã  partir de nâ€™importe lequel des nÅ“uds).

Notes
-----

NoSQL and datagriding are converging. There are not coming from the same world but tends to go the same place ;)


- Plan

1 Introduction  5
1.1 Contexte de l'administration    6
2 Présentation fonctionnelle du domaine 7
2.1 Objectif & Définition   7
2.2 Un peu d'histoire   8
2.3 Principes fondamentaux  8
2.3.1 Le message    9
2.3.2 Transport de messages 9
2.3.3 Routage de messages   10
2.3.4 Les communications    12
2.3.5 Garantie et fiabilité de l'acheminement des messages  14
2.3.6 Transaction   14
2.3.7 Les standards et normes   15
2.3.8 Sécurité  17
2.3.9 Exploitation  18
2.3.10 A propos des performances    21
2.3.11 Concernant les aspects « développement » 22
2.4 Cas de « Atom Publishing Protocol » 23
2.4.1 ATOM  24
2.4.2 APP   24
2.4.3 Principe de fonctionnement    25
2.4.4 Cas d'usage   25
2.4.5 Ressources AtomPub    26
2.5 Principales fonctionnalités attendues   26
2.6 Formalisation des besoins de l'administration via QSOS  33
3 Analyse QSOS  35
3.1 Périmètre   35
3.2 Tendances de recherches sur Google  35
3.3 Apache ActiveMQ 37
3.3.1 Introduction  37
3.3.2 Couverture fonctionnelle  37
3.3.3 Remarques 38
3.4 Apache ActiveMQ « Apollo »  40
3.4.1 Introduction  40
3.4.2 Couverture fonctionnelle  41
3.4.3 Remarques 41
3.5 HornetQ 42
3.5.1 Introduction  42
3.5.2 Couverture fonctionnelle  42
3.5.3 Remarques 43
3.6 Apache Qpid 44
3.6.1 Introduction  44
3.6.2 Couverture fonctionnelle  44
3.6.3 Remarques 45
3.7 RabbitMQ    46
3.7.1 Introduction  46
3.7.2 Couverture fonctionnelle  46
3.7.3 Remarques 47
3.8 ZeroMQ  48
3.8.1 Introduction  48
3.8.2 Couverture fonctionnelle  49
3.8.3 Remarques 49
3.9 JORAM   51
3.9.1 Introduction  51
3.9.2 Couverture fonctionnelle  51
3.9.3 Remarques 52
3.10 Apache Kafka   54
3.10.1 Introduction 54
3.10.2 Couverture fonctionnelle 54
3.10.3 Remarques    55
3.11 Mosquitto  56
3.11.1 Introduction 56
3.11.2 Couverture fonctionnelle 56
3.11.3 Remarques    57
4 Synthèse  58
4.1 Panorama    58
4.2 Couverture fonctionnelle    58
4.3 Couverture fonctionnelle pondérée   60
5 Conclusion    62
6 Méthode QSOS  63
6.1 Critères maturité   64
6.2 Grille de comparaison dynamique 65
6.3 Documents QSOS au format XML




    Introduction
        Contexte de l'administration
    Présentation fonctionnelle du domaine
        Objectif et définition
        Historique
        Principes fondamentaux
            Cache distribuée vs Cache en mémoire
            Cache distribuée vs Datagriding vs NoSQL
            Clustering
            Interfaçage du système de cache avec les applications
        Principales fonctionnalités attendues
        Formation des besoins de l'administration via QSOS
    Analyse QSOS
        Périmètre
        Tendances de recherches sur Google
        Cas 1
            Introduction
            Couverture fonctionnelle
            Remarques
        Cas 2, etc...
    Synthèse
        Panorama
        Couverture fonctionnelle
        Couverture fonctionnelle pondérée
    Conclusion
    Méthode QSOS

