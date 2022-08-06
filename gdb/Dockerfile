FROM debian:bullseye-slim

RUN apt-get update && apt-get upgrade && apt-get install -y \
	gdb gcc libc6-dev \
	--no-install-recommends \
	&& rm -rf /var/lib/apt/lists/*

# Set user and group
ARG user=levtuman
ARG group=gamers
ARG uid=1000
ARG gid=1000
RUN groupadd -g ${gid} ${group}
RUN useradd -u ${uid} -g ${group} -s /bin/sh -m ${user} # <--- the '-m' create a user home directory
ENV HOME /home/${user}

WORKDIR ${HOME}

# COPY factorial.c to workdir
COPY --chown="${user}":"${group}" factorial.c factorial.c

# Switch to user
USER ${uid}:${gid}
