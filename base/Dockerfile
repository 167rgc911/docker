FROM my/anaconda3:2020.11

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN useradd -d /althome/rgc -s /bin/bash rgc && \
    echo rgc:rgc | chpasswd && adduser rgc sudo && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

USER rgc
WORKDIR /althome/rgc

CMD [ "/bin/bash" ]
