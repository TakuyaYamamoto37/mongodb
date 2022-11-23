FROM docker:dind

RUN echo '* * * * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"`' >> /etc/crontab

RUN crontab /etc/crontab
CMD ["sh", "-c", "crond -f"]
