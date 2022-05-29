FROM registry.hpc.ut.ee/mirror/library/alpine

RUN apk add --no-cache python3 py3-pip
RUN pip3 install flask

COPY server.py /opt/server.py

EXPOSE 5000
CMD python3 /opt/server.py