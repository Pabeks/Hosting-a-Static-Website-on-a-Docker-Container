FROM amazonlinux:latest

# Install dependencies
RUN yum update -y && \
    yum install -y httpd git  

# change directory
RUN cd /var/www/html

# Clone the repository
RUN git clone https://github.com/Pabeks/host-a-static-website-on-aws.git

# copy files into html directory
RUN cp -R host-a-static-website-on-aws/. /var/www/html/

# remove unwanted folder
RUN rm -rf host-a-static-website-on-aws

# exposes port 80 on the container
EXPOSE 80

# set the default application that will start when the container start
ENTRYPOINT ["/usr/sbin/httpd", "-D", "FOREGROUND"]