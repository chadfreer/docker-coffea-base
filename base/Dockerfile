FROM continuumio/miniconda3:latest

RUN apt-get update \
     && apt-get install -yq --no-install-recommends libarchive-dev \
     && apt-get clean && rm -rf /var/lib/apt/lists/*

# XRootD + CA + VOMS + Coffea
RUN conda install mamba -n base -c conda-forge --yes
RUN mamba install --yes \
      -c conda-forge \
      conda-build \
      voms \
      jupyterlab \
      ipympl \
      dask_labextension \
      python==3.8.* \
      ca-policy-lcg \
      xrootd==5.3.0 \
      "uproot>=4.0.8" \
      coffea==0.7.8 \
      vector xgboost \
      lz4 python-xxhash zstandard \
     && mamba clean -tipsy \
     && pip install --no-cache-dir "fastjet==3.3.4.0rc9"

# Make a symbolic link between installation /opt/conda/etc/grid-security and actual directory /etc/grid-security
RUN ln -s /opt/conda/etc/grid-security /etc/grid-security
