FROM python:3.7-alpine

# Install AWS CLI
RUN pip install awscli --upgrade

# Install CURL
RUN apk add --no-cache bash curl openssl ca-certificates git ssh

# Install Kubectl
RUN set -ex \
        && curl -o kubectl https://amazon-eks.s3-us-west-2.amazonaws.com/1.10.3/2018-07-26/bin/linux/amd64/kubectl \
        && chmod +x ./kubectl \
        && mv ./kubectl /usr/local/bin/kubectl \
        \
        # Install IAM Authenticator
        && curl -o aws-iam-authenticator https://amazon-eks.s3-us-west-2.amazonaws.com/1.10.3/2018-07-26/bin/linux/amd64/aws-iam-authenticator \
        && chmod +x ./aws-iam-authenticator \
        && cp ./aws-iam-authenticator $HOME/bin/aws-iam-authenticator && export PATH=$HOME/bin:$PATH

ENTRYPOINT ["/bin/bash"]
