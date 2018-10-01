# EOSIO Kafka Plugin
EOSIO Kafka Plugin

## Requirements
###  install librdkafka
```
#cd /usr/local
#git clone https://github.com/edenhill/librdkafka.git
#cd librdkafka
#./configure
#make
#sudo make install
```

## Building the plugin [Install on your nodeos server]
```
#cd /usr/local/eos/plugins/
#git clone https://github.com/shahofblah/kafka_plugin.git

edit /usr/local/eos/plugins/CMakeLists.txt:
#add_subdirectory(kafka_plugin)

edit /usr/local/eos/programs/nodeos/CMakeLists.txt:
#target_link_libraries( nodeos PRIVATE -Wl,${whole_archive_flag} kafka_plugin -Wl,${no_whole_archive_flag} )
```
## How to setup on your nodeos
Enable this plugin using --plugin option to nodeos or in your config.ini. Use nodeos --help to see options used by this plugin.

## Configuration
Add the following to config.ini to enable the plugin:
```
#parameters for kafka_plugin
plugin = eosio::kafka_plugin
kafka-uri = localhost:9092
#topic for transactions
trx_topic = trx
#topic for account creations
acc_topic = acc
kafka-block-start = 100
kafka-queue-size = 5000


