FROM python:3.8-alpine
WORKDIR /app
COPY requirements.txt .
RUN python -m pip install --upgrade pip && pip install -r requirements.txt
COPY . .
EXPOSE 5000
CMD gunicorn --bind 0.0.0.0:5000 app:app
# CMD ["python", "app.py"]