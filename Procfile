web: python plpred/server.py --port $PORT --host 0.0.0.0 --model data/models/models.pickle
worker: celery -a plpred.worker.celery worker