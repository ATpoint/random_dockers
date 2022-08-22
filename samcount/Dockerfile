FROM condaforge/mambaforge:4.13.0-1

RUN apt update && \
    DEBIAN_FRONTEND=noninteractive apt install -y --no-install-recommends nano && \
    apt-get clean

RUN mamba install -c bioconda -c conda-forge -y samtools subread parallel