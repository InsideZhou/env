FROM 'docker.elastic.co/elasticsearch/elasticsearch:7.9.0'

COPY --chown=1000:1000 ./jieba /usr/share/elasticsearch/plugins/jieba
COPY --chown=1000:1000 ./jieba/dic/stopwords.txt /usr/share/elasticsearch/config/stopwords/
