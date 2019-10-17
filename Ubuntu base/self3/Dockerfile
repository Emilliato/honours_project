FROM g19m2952/mars_web:self2
#creating a working directory
RUN cd ../..
ADD MARS.tar.xz .
WORKDIR MARS
CMD ['python', 'manage.py']
