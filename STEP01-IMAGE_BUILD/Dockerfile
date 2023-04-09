FROM python:3.6-alpine
LABEL maintainer="Younes AIT-JEBLI - eazytraining student"
WORKDIR /opt
RUN  pip install flask
ADD . .
EXPOSE 8080
ENV ODOO_URL="https://www.odoo.com/" PGADMIN_URL="https://www.pgadmin.org/"
ENTRYPOINT ["python", "app.py"]
