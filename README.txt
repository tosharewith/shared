================================================================================
Universal Translator - Delivery Package
================================================================================

CONTENTS
--------
ut-01-core-visualizer-bff.zip    (601 KB)  - Visualizer + BFF source
ut-02-go-service.zip             (6.7 MB)  - Go COMEX service
ut-03-java-service.zip           (20 KB)   - Java Spring Boot service
ut-04-templates.zip              (9.9 MB)  - Project generation templates
ut-05-extractions-aa to -al      (164 MB)  - Transaction data (12 parts)

TOTAL: ~181 MB (split into files <15MB each)

================================================================================
INSTALLATION INSTRUCTIONS
================================================================================

1. EXTRACT CORE PACKAGES
------------------------
   unzip ut-01-core-visualizer-bff.zip
   unzip ut-02-go-service.zip
   unzip ut-03-java-service.zip
   unzip ut-04-templates.zip

2. REASSEMBLE EXTRACTIONS (required for visualizer)
---------------------------------------------------
   # On Linux/macOS:
   cat ut-05-extractions-* > extractions-combined.zip
   unzip extractions-combined.zip
   rm extractions-combined.zip

   # On Windows (PowerShell):
   Get-Content ut-05-extractions-* -Encoding Byte -ReadCount 0 | Set-Content extractions-combined.zip -Encoding Byte
   Expand-Archive extractions-combined.zip -DestinationPath .

3. INSTALL DEPENDENCIES
-----------------------
   # Visualizer
   cd universal/visualizer
   npm install

   # BFF
   cd bff
   npm install

================================================================================
RUNNING THE APPLICATIONS
================================================================================

VISUALIZER (Frontend)
---------------------
   cd universal/visualizer
   npm run dev
   # Opens at http://localhost:3000

BFF (Backend for Frontend)
--------------------------
   cd bff
   npm run dev
   # Runs at http://localhost:3001

GO SERVICE
----------
   cd projects/comex-service
   make run
   # Or: go run ./cmd/main.go
   # Runs at http://localhost:8080

JAVA SERVICE
------------
   cd projects/comex-service-java
   ./mvnw spring-boot:run
   # Or: mvn spring-boot:run
   # Runs at http://localhost:8080

================================================================================
DOCKER BUILD
================================================================================

Each service includes a Dockerfile for containerization:

   # Go Service
   cd projects/comex-service
   docker build -t comex-service .
   docker run -p 8080:8080 comex-service

   # Java Service
   cd projects/comex-service-java
   docker build -t comex-service-java .
   docker run -p 8080:8080 comex-service-java

================================================================================
KUBERNETES DEPLOYMENT
================================================================================

Each service includes k8s/ directory with manifests:

   kubectl apply -k projects/comex-service/k8s/
   kubectl apply -k projects/comex-service-java/k8s/

================================================================================
