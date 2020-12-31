## AestheticPredictorSharedFlaskApi

AestheticPredictorSharedFlaskApi is a python tool which offers a unified Flask interface for aesthetic metric predictors.

### Requirements

This project requires Python 3.


### Installation

Run:

```bash
pip install aesthetic-predictor-flask-api
```
 
### Usage

After installation run the following command with two parameters:
```bash
python -m aesthetics_predictor_api_pkg.config_files_creation --predictor dotted.path.to.predictor.class --port port_num
```

- dotted.path.to.predictor.class: path to the predictor class from the project root (Example: src.main_predictor_module.MainPredictorClass). 
Ensure that the class implements a method with the following signature and name: 
```python
def predict(self, content_path: str, start_frame: int = 0, end_frame: int = 0) -> flask.Response:
```
- port_num: define on which port the flask server should listen to.


To start the Flask Api on Gunicorn, run the following command:

```bash
gunicorn --config gunicorn_config.py --env API_CONFIG=api_config.json aesthetics_predictor_api_pkg.predictor_api_server:app
```