FROM ubuntu:latest

# update
RUN apt-get -y update && apt-get install -y \
sudo \
wget \
vim

#install anaconda3
WORKDIR /opt
# download anaconda package and install anaconda
# archive -> https://repo.continuum.io/archive/
RUN wget https://repo.continuum.io/archive/Anaconda3-2019.10-Linux-x86_64.sh && \
sh /opt/Anaconda3-2019.10-Linux-x86_64.sh -b -p /opt/anaconda3 && \
rm -f Anaconda3-2019.10-Linux-x86_64.sh

# set path
ENV PATH /opt/anaconda3/bin:$PATH

# update pip and conda
RUN pip install --upgrade pip \
    ptitprince\
    pandas_profiling\
    pandas==0.25.1\
    lightgbm

WORKDIR /
RUN mkdir /work

COPY ipaexg.ttf  /opt/anaconda3/lib/python3.7/site-packages/matplotlib/mpl-data/fonts/ttf

RUN echo 'font.family : IPAexGothic' >> /opt/anaconda3/lib/python3.7/site-packages/matplotlib/mpl-data/matplotlibrc

# RUN rm -r ./.cache

# execute jupyterlab as a default command
CMD ["jupyter", "lab", "--ip=0.0.0.0", "--allow-root", "--LabApp.token=''"]