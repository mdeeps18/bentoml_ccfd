## Deploy ml Model to detect credit card fraud detection with Bentoml

```bash
git clone https://github.com/Devendra61/bentoml_ccfd.git 
``` 
```bash 
cd bentoml_ccfd && pip install -r requirements.txt
``` 
```bash
python3 train.py 
```
```bash
bentoml serve service.py:svc --reload
```
#### replace <instance_public_ip>  with your <machine_public_ip> example: https://54.237.70.93:8080/

#### https://<instance_public_ip>:8080/

