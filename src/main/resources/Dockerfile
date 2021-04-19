FROM quay.io/gmeder/acebuilder:1.0 AS build
ENV APP_NAME=SampleApp
COPY --chown=1000:1000 src/main/ace/ /home/aceuser/workspace
RUN Xvfb -ac :99 & \
    DISPLAY=":99" /opt/ibm/ace-11/tools/mqsicreatebar \
    -data /home/aceuser/workspace/ -b /home/aceuser/workspace/${APP_NAME}.bar \
    -a $APP_NAME  -cleanBuild -deployAsSource

FROM ibmcom/ace-server
COPY --from=build /home/aceuser/workspace/*.bar /home/aceuser/initial-config/bars/