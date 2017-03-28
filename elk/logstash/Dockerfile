FROM localhost:5000/logstash:5.2.2
COPY nginx-syslog.conf /nginx-syslog.conf
EXPOSE 5000
CMD ["logstash", "-f", "/nginx-syslog.conf"]