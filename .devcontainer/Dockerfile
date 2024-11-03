# This Dockerfile extends texlive by installing python and configuring a default miniconda environment

FROM texlive/texlive:latest-full

# Install necessary packages
RUN apt-get update && apt-get install -y \
    git \
    perl \
    wget \
    bzip2 \
    openssh-server \
    ca-certificates \
    curl \
    && rm -rf /var/lib/apt/lists/* \
    && apt-get clean \
    && apt-get autoremove -y \
    && rm -rf /var/lib/apt/lists/* \
    && rm -rf /tmp/*

# Install Miniconda
ENV CONDA_DIR /opt/conda
RUN wget --quiet https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O ~/miniconda.sh && \
    /bin/bash ~/miniconda.sh -b -p /opt/conda && \
    rm ~/miniconda.sh && \
    ln -s /opt/conda/etc/profile.d/conda.sh /etc/profile.d/conda.sh && \
    echo ". /opt/conda/etc/profile.d/conda.sh" >> ~/.bashrc && \
    echo "conda activate base" >> ~/.bashrc
ENV PATH $CONDA_DIR/bin:$PATH

# Creates the "math-env" environment and sets it as default
RUN conda create -n math-env python=3.9 -y
ENV CONDA_DEFAULT_ENV math-env

# Add the python packages you need here
RUN conda run -n math-env conda install -y \
    numpy \
    matplotlib \
    tqdm \
    seaborn

# Cache cleanup
RUN conda clean --all -a -y \
    && conda run -n math-env pip cache purge \
    && rm -rf ~/.cache/pip

# Activate math-env environment by default
RUN echo "conda activate math-env" >> ~/.bashrc

RUN echo "Welcome to this test environment for working in mathematics with LaTeX and Python"
CMD ["/bin/bash"]
