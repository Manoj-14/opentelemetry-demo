FROM golang:1.24-alpine AS builder

WORKDIR /usr/src/app/


# Copy source code
COPY . .

# Download binaries
RUN go mod download

#build the code and get artifact

RUN go build -o product-catalog .

####################################

FROM alpine AS release

WORKDIR /usr/src/app/

COPY ./products ./products
COPY --from=builder /usr/src/app/product-catalog/ ./

ENV PRODUCT_CATALOG_PORT=8089

ENTRYPOINT [ "./product-catalog" ]
