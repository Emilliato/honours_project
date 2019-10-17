FROM continuumio/miniconda3:4.6.14

# Install extra packages if required
RUN apt-get update  && apt-get install -y \
   libpq-dev \
   build-essential \
   && rm -rf /var/lib/apt/lists/*

#Add the user that will run the app (no need to run as root)

RUN groupadd -r mars_user && useradd -r -g mars_user mars_user


RUN apt-get install -y libgl1-mesa-glx apt-utils openssh-server net-tools


WORKDIR /code


COPY environment.yml /code/environment.yml

#Conda update and creation of environment
RUN conda config --add channels defaults

RUN conda config --add channels bioconda

RUN conda config --add channels conda-forge

RUN pip install --upgrade pip
# conda update -n base -c defaults conda
RUN conda update conda && \
    conda env create -f environment.yml && \
    conda activate MARS\
    echo "conda activate MARS" && \
    rm -rf /opt/conda/pkgs/*
COPY . /code/
RUN chown -R mars_user:mars_user /code/*
ENV PATH /opt/conda/envs/MARS/bin:$PATH
CMD ["python","/code/manage.py"]
