FROM microsoft/vsts-agent:ubuntu-16.04-docker-17.12.0-ce-standard
ADD https://github.com/armbuild/qemu-user-static/raw/master/x86_64/qemu-arm-static /usr/local/bin/
RUN mount binfmt_misc -t binfmt_misc /proc/sys/fs/binfmt_misc && test -f /proc/sys/fs/binfmt_misc/arm && echo "binfmt already registered" > &2 || echo ':CLR:M::MZ::/usr/bin/mono:' > /proc/sys/fs/binfmt_misc/register
RUN apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 3FA7E0328081BFF6A14DA29AA6A19B38D3D831EF && \
echo "deb http://download.mono-project.com/repo/ubuntu xenial main" | tee /etc/apt/sources.list.d/mono-official.list && \
apt-get update && \
apt-get install -y mono-runtime && \
rm -rf /var/lib/apt/lists
