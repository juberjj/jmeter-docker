FROM alpine
#LABEL Description="This image is used to start the Apache JMeter Master Executable" 
# Installig Pre-requisite Packages JRE && unzip
RUN apk update && \
       apk -q add \
                        ca-certificates wget\
                        openjdk8-jre \
                        unzip
# Installing jmeter
RUN   mkdir /jmeter \
        && cd /jmeter/ \
        && wget https://archive.apache.org/dist/jmeter/binaries/apache-jmeter-3.2.tgz \
        && tar -xzf apache-jmeter-3.2.tgz \
        && rm apache-jmeter-3.2.tgz \
        && mkdir /jmeter-plugins \
        && cd /jmeter-plugins/ \
        && wget http://jmeter-plugins.org/files/JMeterPlugins-ExtrasLibs-1.4.0.zip \
        && unzip -o JMeterPlugins-ExtrasLibs-1.4.0.zip -d /jmeter/apache-jmeter-3.2/ \
        && wget http://jmeter-plugins.org/files/packages/jpgc-json-2.6.zip \
        && unzip -o jpgc-json-2.6.zip -d /jmeter/apache-jmeter-3.2/
# Settingt Jmeter Home
ENV JMETER_HOME /jmeter/apache-jmeter-3.2/
# Finally Adding Jmeter to the Path
ENV PATH $JMETER_HOME/bin:$PATH
