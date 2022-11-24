FROM docker:dind

# 分　時　日　月　曜日  0と7は日曜日
# RUN echo '* * * * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"` -u=$MONGO_USERNAME -p=$MONGO_PASSWORD' >> /etc/crontab
RUN echo '50 2 */1 * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"`_daily -u=$MONGO_USERNAME -p=$MONGO_PASSWORD' >> /etc/crontab
RUN echo '50 2 */7 * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"`_weekly -u=$MONGO_USERNAME -p=$MONGO_PASSWORD' >> /etc/crontab
RUN echo '50 2 */30 * * docker exec -t cr-mongo mongodump --host="localhost:27017" -o /backup/`date "+%Y%m%d_%H%M%S"`_monthly -u=$MONGO_USERNAME -p=$MONGO_PASSWORD' >> /etc/crontab

RUN crontab /etc/crontab
CMD ["sh", "-c", "crond -f"]
