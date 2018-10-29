# Kafka_Handson

Kafkaのハンズオンを実施した際のVagrantファイル等

## tl;dr

KafkaクラスタをZookeeperアンサンブル構成を用いて構成できます。

## 前提

- OS:Windows10(64bit)
    - おそらくMacでもLinuxでも64bitOSであれば使用できると思います。
- 以下のアプリケーションが使用できること
    - Vagrant
        - https://www.vagrantup.com/downloads.html
    - VirtualBox
        - https://www.virtualbox.org/wiki/Downloads
    - Git
        - https://git-scm.com/downloads

## つかいかた

適当な場所にgit cloneしてvagrant upしてください。

node01～node03の3台のVMが立ち上がります。

例：Windows10

    > cd c:\
    > mkdir git
    
    > git clone https://github.com/t-yamada/Kafka_Handson.git
    > cd Kafka_Handson
    > vagrant up

各nodeで

    $ sudo su
    # cd /opt/kafka
    # bin/zookeeper-server-start.sh -daemon config/zookeeper.properties
    # bin/kafka-server-start.sh -daemon config/server.properties

を実行することでKafkaクラスタが起動します。

## 注意

Kafkaがデフォルトでメモリを1G要求するので、各VMに2Gのメモリを割り当てる設定になっています。
メモリが足りない場合はKafkaの起動前に

    # export KAFKA_HEAP_OPTS="-Xmx256M -Xms256M"

するなどして、Kafkaが使用するメモリを減らしてください。
