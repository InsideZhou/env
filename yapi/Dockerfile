FROM 'mongo:4.2'

RUN sed -i 's/archive.ubuntu.com/mirrors.ustc.edu.cn/g' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y curl git build-essential && \
    curl -sL https://deb.nodesource.com/setup_12.x | bash - && \
    apt-get install -y nodejs

COPY npmrc ~/.npmrc
RUN npm install --registry https://registry.npm.taobao.org -g yapi-cli pm2

WORKDIR /opt/yapi
RUN curl -O https://file.example.com/yapi/vendors.zip
RUN apt-get install -y unzip && unzip vendors.zip

WORKDIR /opt/yapi/vendors
RUN npm install --registry https://registry.npm.taobao.org --unsafe-perm --production

WORKDIR /opt/yapi
COPY config.json /opt/yapi/config.json
COPY entrypoint /opt/yapi/entrypoint
RUN chmod +x ./entrypoint
ENTRYPOINT [ "./entrypoint" ]