to delete a topic:
./bin/kafka-topics.sh --zookeeper localhost:2181 --delete --topic  [topic name]

to get list of topics:
./bin/kafka-topics.sh --zookeeper localhost:2181 --list

if topic is still present (and 'marked for deletion'):
./bin/zookeeper-shell.sh localhost:2181 rmr /brokers/topics/[topic name]

in addition the following might also help (run in zookeeper-shell):
rmr /admin/delete_topics/[topic name]
