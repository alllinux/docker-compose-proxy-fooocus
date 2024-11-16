ARG PYTORCH_VERSION

FROM ${PYTORCH_VERSION}

RUN mkdir -p /usr/app/src
RUN apt-get update && apt-get install -y git \
    libgl1-mesa-glx \
    libglib2.0-0 \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /usr/app/src

RUN git clone https://github.com/lllyasviel/Fooocus.git . && \
    /bin/bash -c "pip install --upgrade pip" && \
    /bin/bash -c "conda env create -f environment.yaml" && \
    python3 -m venv fooocus_env && \
    /bin/bash -c "source fooocus_env/bin/activate && pip install -r requirements_versions.txt"

#RUN chown -R 1000:root /usr/app/src/outputs && \
#    chmod -R 777 /usr/app/src/outputs

EXPOSE 7865

CMD ["/bin/bash", "-c", "source fooocus_env/bin/activate && python entry_with_update.py --listen"]
# CMD ["/bin/bash", "-c", "source fooocus_env/bin/activate && python entry_with_update.py --preset anmie --listen"]
# CMD ["/bin/bash", "-c", "source fooocus_env/bin/activate && python entry_with_update.py --preset realistic --listen"]
