FROM public.ecr.aws/amazonlinux/amazonlinux:2023
RUN dnf update -y \
    && dnf install nginx -y \
    && dnf install nginx-mod-stream -y \
    && dnf install net-tools -y \
    && dnf install iputils -y \
    && dnf install procps -y \
    && dnf install htop -y \
    && mv /etc/nginx/nginx.conf /etc/nginx/nginx.conf.orig
COPY nginx.conf /etc/nginx/
COPY ipcontrol.conf /etc/nginx
RUN ln -sf /dev/stdout /var/log/nginx/http_access.log \
    && ln -sf /dev/stderr /var/log/nginx/http_error.log \
	&& ln -sf /dev/stdout /var/log/nginx/stream_access.log \
    && ln -sf /dev/stderr /var/log/nginx/stream_error.log
CMD ["nginx", "-g", "daemon off;"]
