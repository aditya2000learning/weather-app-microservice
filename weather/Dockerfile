FROM python:3.9.18-alpine
WORKDIR /app
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt
COPY . .
EXPOSE 5000
ENTRYPOINT ["python3"]
CMD [ "main.py" ]