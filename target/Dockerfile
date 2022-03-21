### build stage ###
FROM ubuntu:18.04 as builder
RUN apt update && \
    apt install -y git make yasm as31 nasm binutils && \
    git clone https://github.com/nemasu/asmttpd.git && \
    cd asmttpd && \
    make release 

### run stage ###
FROM scratch
COPY --from=builder /asmttpd/asmttpd /asmttpd
COPY ./contents /web_root
CMD ["/asmttpd", "/web_root", "80"] 