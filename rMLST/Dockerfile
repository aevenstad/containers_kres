FROM python:3.12-alpine3.22

# Install system dependencies
RUN apk update && apk add --no-cache procps wget

# Upgrade setuptools
RUN pip install --no-cache-dir --upgrade setuptools

# Install Python dependencies
RUN pip install --no-cache-dir requests

# Download species_api_upload.py script created by https://github.com/kjolley
RUN mkdir -p /opt/rMLST
RUN wget https://gist.githubusercontent.com/kjolley/703fa2f00c3b2abeef9242fa193ea901/raw/b40d8f999b675d40a48078d0a58302d16df97b04/species_api_upload.py
RUN chmod +x species_api_upload.py
RUN mv species_api_upload.py /opt/rMLST/species_api_upload.py

# Add rMLST to PATH
ENV PATH="$PATH:/opt/rMLST"

