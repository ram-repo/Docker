FROM mcr.microsoft.com/dotnet/aspnet:latest
ARG workspace=nopCommerce
ARG nopCommerce_version=4.60.3
RUN mkdir /var/www && mkdir /var/www/${workspace}
WORKDIR /var/www/${workspace}
RUN apt-get update && apt-get install -y unzip
ADD https://github.com/nopSolutions/nopCommerce/releases/download/release-${nopCommerce_version}/nopCommerce_${nopCommerce_version}_NoSource_linux_x64.zip .
RUN unzip nopCommerce_${nopCommerce_version}_NoSource_linux_x64.zip && \
    rm nopCommerce_${nopCommerce_version}_NoSource_linux_x64.zip
# Add user "nop" with a specified UID
RUN groupadd -r nop && useradd -r -g nop -d /var/www/${workspace} -s /sbin/nologin -u 1001 nop
RUN chown -R nop:nop /var/www/${workspace}
USER nop
EXPOSE 80
CMD ["dotnet", "Nop.Web.dll"]
