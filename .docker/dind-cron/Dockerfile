FROM docker:dind

# 分　時　日　月　曜日  0と7は日曜日
# RUN echo '* * * * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"`' >> /etc/crontab
RUN echo '*/10 * * * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"`' >> /etc/crontab

RUN crontab /etc/crontab
CMD ["sh", "-c", "crond -f"]
