# Kafka_Handson

Kafkaのハンズオンを実施した際のVagrantファイル等

## tl;dr

KafkaクラスタをZookeeperアンサンブル構成を用いて構成できます。

## 前提

- OS:Windows10(64bit)
- Vagrant,VirtualBox,gitが使用できること。

## つかいかた

適当な場所にgit cloneしてvagrant upしてください。

node01～node03の3台のVMが立ち上がります。

各nodeで

    $ sudo su
    # cd /opt/kafka
    # bin/zookeeper-server-start.sh -daemon config/zookeeper.properties
    # bin/kafka-server-start.sh -daemon config/server.properties

を実行することでKafkaクラスタが起動します。

## 注意

Kafkaがデフォルトでメモリを1G要求するため、1つのVMに2Gの割当になっています。
メモリが足りない場合はKafkaの起動前に

    # export KAFKA_HEAP_OPTS="-Xmx256M -Xms256M"

するなどして使用メモリを減らしてください。
