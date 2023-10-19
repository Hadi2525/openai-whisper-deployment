FROM python:3.10.13

# Install Miniconda
RUN wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh -O miniconda.sh && \
    bash miniconda.sh -b -p /opt/conda && \
    rm miniconda.sh

# Add conda to PATH
ENV PATH="/opt/conda/bin:${PATH}"

# Copy the dependencies file to the working directory
COPY requirements.txt .

# Install packages
RUN pip install -U openai-whisper flask boto3 botocore
RUN pip install -r requirements.txt
RUN conda install -y ffmpeg

# Copy server script
COPY asr_server.py /opt/program/

# Set working directory
WORKDIR /opt/program

# Set the entrypoint
ENTRYPOINT ["python", "asr_server.py"]
