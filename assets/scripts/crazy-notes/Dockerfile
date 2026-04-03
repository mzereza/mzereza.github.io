FROM ubuntu@sha256:353675e2a41babd526e2b837d7ec780c2a05bca0164f7ea5dbbd433d21d166fc

RUN apt-get update
RUN apt-get upgrade -y
RUN apt-get install -y socat
RUN useradd -m ctf

WORKDIR /home/ctf

COPY ./flag.txt /home/ctf/flag.txt
COPY ./chall /home/ctf/chall
COPY libc.so.6 ld-linux-x86-64.so.2 .

RUN chown -R ctf:ctf /home/ctf/

USER ctf

CMD socat TCP-LISTEN:5011,reuseaddr,fork EXEC:"timeout 60 /home/ctf/chall,stderr"