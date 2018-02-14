FROM centos/postgresql-94-centos7:latest

USER root

RUN yum install -y epel-release && \
    DEVEL_PACKAGES="gcc-c++ make libxml2-devel rh-postgresql94-postgresql-devel geos-devel proj-devel gdal-devel" &&
    yum install -y $DEVEL_PACKAGES && \
    curl -sL http://download.osgeo.org/postgis/source/postgis-2.2.2.tar.gz | tar xzvf - -C /tmp && \
    scl enable rh-postgresql94 'cd /tmp/postgis-2.2.2 && ./configure && make && make install' && \
    rm -rf /tmp/postgis-2.2.2 && \
    yum remove -y $DEVEL_PACKAGES && \
    yum clean all

USER 26
