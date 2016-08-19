# Alpine Linux miniconda with Redash

FROM youske/alpine-nodejs-python:python2
MAINTAINER youske miyakoshi <youske@gmail.com>

ENV REDASH_HOME=/redash \
    PORT=8888

ENV PACKAGE='sudo gawk git pwgen freetds ' \
    BUILD_PACKAGE='build-base musl-dev linux-headers libffi-dev python-dev nodejs-dev util-linux-dev' \
    CONDA_PACKAGE='jupyter matplotlib dateutil pyyaml pymysql sqlalchemy psycopg2 pandas scipy numpy cython bokeh xlrd xlutils openpyxl ipywidgets' \
    PIP_PACKAGE='psutil jupyter_cms metakernel_bash metakernel_python redis_kernel pandas-td pandas-datareader ' \
    WIDGET_PACKAGE='ipyleaflet bqplot pythreejs'

# Users creation
RUN addgroup redash && adduser -S -G redash redash


RUN apk update upgrade --no-cache
RUN apk add ${PACKAGE} --no-cache
RUN apk add ${BUILD_PACKAGE} --no-cache -t buildpack

COPY requirements.txt /tmp/

#RUN REDASH_VERSION=${REDASH_VERSION-0.11.1.b2095} && \
#    LATEST_URL="https://github.com/getredash/redash/releases/download/v${REDASH_VERSION}/redash.${REDASH_VERSION}.tar.gz" && \
#    wget ${LATEST_URL}

#RUN wget https://deb.nodesource.com/setup_4.x -O- | bash -
#RUN conda update -q -y conda && conda install -y ${CONDA_PACKAGE} && conda clean -itpsly
#RUN cd /tmp && pip install -r requirements.txt

# remove buildpack
#RUN apk del buildpack --no-cache && rm -rf /tmp/* /var/cache/apk/*

EXPOSE ${PORT}
