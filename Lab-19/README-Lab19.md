# AWS Solutions Architect Associate - Laboratorio 19

<br>

### Objetivo: 
* Configuración de los "Routing Policies Latency & Weighted" en Route 53

### Tópico:
* Networking
* Content Delivery

### Dependencias:
* Será necesario contar con un Dominio creado en Route53

### Costo:
* El uso de Route 53 tiene un costo asociado.

<br>

---

### A - Configuración de los "Routing Policies Latency & Weighted" en Route 53

<br>

1. Generar Keys Pair en las regions de **N.Virginia (us-east-1)** y **Paris (eu-west-3)**. De no ser así, acceder al servicio EC2 y luego a la opción "Key Pair" de cada región indicada. Generar llave RSA y .pem 

2. Acceder al servicio AWS Cloud9 en N.Virginia y generar un nuevo ambiente de trabajo (Ubuntu 18.04 LTS)

3. Ejecutar los siguientes comandos en nuestro Cloud9

```bash
#Ubuntu 18.04
sudo apt-get update
git clone https://github.com/jbarreto7991/aws-solutionsarchitectassociate.git
```

4. Acceder al laboratorio 15 (Lab-15), carpeta "code". Validar que se cuenta con tres archivos CloudFormation: "1_lab15-vpc.yaml", "2_lab15-ec2.yaml" y "3_lab15_alb_targetgroup". Analizar el contenido de estos archivos.

5. Desplegar cada plantilla CloudFormation ejecutando AWSCLI. Considerar los parámetros a ser ingresados.

    <br>
6. **1_lab15-vpc.yaml** (Esperar el despliegue total de esta plantilla cloudformation para continuar con las siguientes plantillas). En la sección "ParameterValue", ingresar el nombre del KeyPair creado en el paso 1. Esta plantilla creará la VPC "192.168.0.0/16", 06 Subnets dentro de este CIDR, un NAT Instances y demás componentes de red. No deberán existir redes existentes en este rango de IPs. Validar la creación del Stack desde la consola AWS a través del servicio AWS CloudFormation. El siguiente comando considera el valor "aws-solutionsarchitectassociate" para el KeyPair, reemplazar el nombre según la llave respectiva.

```bash
aws cloudformation create-stack --stack-name lab15-vpc --template-body file://~/environment/aws-solutionsarchitectassociate/Lab-15/code/1_lab15-vpc.yaml --parameters ParameterKey=KeyPair,ParameterValue="aws-solutionsarchitectassociate" --capabilities CAPABILITY_IAM
```




### Eliminación de recursos

```bash
aws cloudformation delete-stack --stack-name lab15-alb-targetgroup
```