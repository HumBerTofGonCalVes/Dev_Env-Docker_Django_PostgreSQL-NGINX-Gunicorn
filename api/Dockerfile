# pull official base image
FROM python:3.12-alpine3.19

COPY /api /api

# set work directory
WORKDIR /api

# set environment variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# install dependencies
RUN pip install --upgrade pip
COPY /api/requirements.txt .
RUN pip install -r /api/requirements.txt

# copy entrypoint.sh
COPY /entrypoint.sh .
RUN sed -i 's/\r$//g' /api/entrypoint.sh
RUN chmod +x /api/entrypoint.sh

# copy project
COPY . .

# run entrypoint.sh
CMD ["entrypoint.sh"]