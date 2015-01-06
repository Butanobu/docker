# Import a tar file using the following method first:

# http://docs.docker.com/articles/baseimages/

# This dockerfile uses ubuntu trusty as the base, without uploading to a
# registry first.

FROM dockerreg:5000/base/ubuntu:14.04_ootb

# There are some files we need to add. If you need to add more files,
# put them in a directory structure in the base folder this Dockerfile
# is in, then append them to the tar file. Use sudo to maintain permissions
# when you add them to the tar file.

ADD trusty.tar /

# Upgrade all packages, just in case, then install a few packages everyone
# is likely to need.

# Using backslashes allows us to split the run command over multiple lines.

# Using double-ampersand links command one after another on one
# command line.

# Making the RUN command like this minimises the number of intermediate
# images we create.

# The "apt-get clean" and "rm" cleans up afterwards to save a bit of space in the base image.

RUN \
  apt-get update && \
  apt-get -y upgrade && \
  apt-get install -y update-manager-core build-essential software-properties-common curl man unzip vim wget && \
  apt-get clean && \
  rm -rf /var/lib/apt/lists/*
