FROM ubuntu:bionic

ENV LANG=C.UTF-8 LC_ALL=C.UTF-8
ENV PATH /opt/conda/bin:$PATH

RUN apt-get update --fix-missing && \
    apt-get install -y wget bzip2 ca-certificates libglib2.0-0 git mercurial subversion \
        software-properties-common gpg libxext6 libsm6 libxrender1 libxcomposite1 libxcursor1 libxss1 libegl1 freeglut3 \
        basex sudo vis loksh && \
    apt-get clean

RUN useradd -d /althome/rgc -s /bin/bash rgc && \
    echo rgc:rgc | chpasswd && adduser rgc sudo && \
    echo '%sudo ALL=(ALL) NOPASSWD:ALL' >> /etc/sudoers

RUN wget --quiet https://repo.anaconda.com/archive/Anaconda3-2020.11-Linux-x86_64.sh -O ~/anaconda.sh && \
    /bin/bash ~/anaconda.sh -b -p /opt/conda && \
    rm ~/anaconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc && \
    find /opt/conda/ -follow -type f -name '*.a' -delete && \
    find /opt/conda/ -follow -type f -name '*.js.map' -delete && \
    /opt/conda/bin/conda clean -afy


USER rgc
WORKDIR /althome/rgc

CMD [ "/bin/bash" ]
