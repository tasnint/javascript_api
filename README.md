# Microservices with FastAPI and Redis

This repository contains a set of microservices implemented using FastAPI and Redis. The services handle order processing, product management, and real-time updates using Redis streams.

## Payment Service (payment/main.py)
This service handles order creation and management. It includes endpoints to create an order and retrieve order details. When an order is created, it sends a background task to mark the order as completed after a delay.

## Payment Consumer (payment/consumer.py)
This script listens for refund events from a Redis stream and processes them by updating the order status to 'refunded'.

## Inventory Service (inventory/main.py)
This service manages product information. It includes endpoints to create, retrieve, and delete products.

## Inventory Consumer (inventory/consumer.py)
This script listens for order completion events from a Redis stream and updates the product inventory accordingly. If the inventory update fails, it sends a refund event to the appropriate stream.


