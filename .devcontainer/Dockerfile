# Use the 'verse' image (includes R, tidyverse, RMarkdown, LaTeX, pandoc, and RStudio Server)
FROM rocker/verse:latest

# Install C++ tools and Quarto CLI
RUN apt-get update && apt-get install -y \
    build-essential \
    libcurl4-openssl-dev \
    libssl-dev \
    libxml2-dev \
    libgit2-dev \
    cmake \
    libclang-dev \
    wget && \
    wget https://quarto.org/download/latest/quarto-linux-amd64.deb && \
    dpkg -i quarto-linux-amd64.deb && \
    rm quarto-linux-amd64.deb

# Optional: create a working directory
WORKDIR /home/rstudio/project

# Make sure RStan works with recent toolchain
RUN echo "CXX14FLAGS=-O3 -march=native -mtune=native -fPIC" >> /usr/local/lib/R/etc/Makeconf && \
    echo "CXX14=g++" >> /usr/local/lib/R/etc/Makeconf
