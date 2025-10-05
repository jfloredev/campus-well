FROM python:3.12-slim
WORKDIR /app

RUN apt-get update && apt-get install -y default-mysql-client && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
EXPOSE 8082


RUN echo '#!/bin/bash\n\
echo "=== Sports Service Startup ==="\n\
echo "🚀 Starting sports service..."\n\
exec uvicorn main:app --host 0.0.0.0 --port 8082' > /app/start.sh

RUN chmod +x /app/start.sh
CMD ["/app/start.sh"]