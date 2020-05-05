<h1 align="center">
  <b>BERT</b>
</h1>

<p align="center">
  📄 Evidence Retrieval and Claim Verification for the FEVER shared task using Transformer Networks
  <br/>

  <sub>
    Available pre-trained models: Bert
  </sub>
</p>

# FEVER Shared Task
The [FEVER Shared Task][link:fever] is a task in which participants are asked to classify a `claim` (e.g. "The number 42 is the Answer to the Ultimate Question of Life, the Universe, and Everything") into `SUPPORTS`, `REFUTES` or `NOT ENOUGH INFORMATION` while also providing the relevant evidence sentences from Wikipedia (only).

## Run the pipeline

If you want to run it locally, you need to run the following commands.

```bash
# Install pipenv (i.e. a better python package manager).
pip3 install pipenv

# Download the source code from GitHub and cd into the folder.


# Run the entire pipeline (it also installs the required dependencies).
bash scripts/pipeline.sh
```

> NB: The only requirement to run the mentioned commands, is that you have python3 and pip3 installed on your machine. You can also skip the pipenv installation if you already have it on your machine.

Alternatively, the CLI allows you to run the single tasks individually as follows.

```bash
# Install required dependencies in a virtual environment.
bash scripts/pipeline.sh install_deps

# Download the fever shared task.
bash scripts/pipeline.sh download_fever

# Build an sql database using the fever wikipedia dump.
bash scripts/pipeline.sh build_db

# Process the datasets for document retreival
bash scripts/pipeline.sh document_retrieval

# Process the datasets through the transformer network sentence retrieval model.
# See below for the possible values of model type and name.
bash scripts/pipeline.sh sentence_retrieval --model-type bert --model-name bert-base-cased

# Process the datasets through the transformer claim verification model.
# See below for the possible values of model type and name.
bash scripts/pipeline.sh claim_verification --model-type bert --model-name bert-base-cased

# Combine the results from the previous steps to generate the final submission files.
bash scripts/pipeline.sh generate_submission --force
```

