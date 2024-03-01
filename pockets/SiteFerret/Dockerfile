# https://github.com/maliksahil/docker-ubuntu-sahil

FROM ubuntu:22.04
LABEL maintainer="maintainer"

#RUN apt-get update && \
#    apt-get install -y python3-pip python3.8-dev python3-setuptools  

RUN apt-get update && \
    apt-get install -y python3-pip python3.8-dev python3-setuptools sudo curl git-core gnupg locales nodejs zsh wget nano nodejs npm fonts-powerline && \
    locale-gen en_US.UTF-8  && \
    adduser --quiet --disabled-password --shell /bin/zsh --home /home/devuser --gecos "User" devuser && \
    echo "devuser:password" | chpasswd &&  usermod -aG sudo devuser


#RUN apt-get update && \
#    apt-get install -y sudo curl git-core gnupg locales nodejs zsh wget nano nodejs npm fonts-powerline && \
#    locale-gen en_US.UTF-8  && \
#    adduser --quiet --disabled-password --shell /bin/zsh --home /home/devuser --gecos "User" devuser && \
#    echo "devuser:password" | chpasswd &&  usermod -aG sudo devuser

# python3-pip
RUN apt-get install -y  

RUN sudo git clone https://github.com/concept-lab/SiteFerret.git && \
    cd SiteFerret/install_binaries && \
    sudo ./install_script && \
    cd .. && \
    sudo pip3 install -e . && \
    sudo mkdir structures
    
RUN sudo pip install Cython==0.29.36 pdb2pqr numpy scipy
RUN sudo pip install scikit-learn==0.24.2 --no-build-isolation



ADD scripts/installthemes.sh /home/devuser/installthemes.sh
USER devuser
ENV TERM xterm
ENV ZSH_THEME agnoster
CMD ["zsh"]

#wget https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh -O - | zsh 