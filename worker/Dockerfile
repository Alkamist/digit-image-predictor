# ====================== Build stage ======================
FROM alkamist1/odin:latest AS builder

RUN apt-get update && apt-get install -y \
    libssl-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /app

COPY . .

RUN odin build . -out:app



# ====================== Runtime stage ======================
FROM ubuntu:24.04

WORKDIR /app

COPY --from=builder /app/app .
COPY model.json /app/model.json

CMD ["./app"]
