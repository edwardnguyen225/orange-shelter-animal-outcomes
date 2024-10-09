# Shelter Animal Outcomes Prediction Project

This repository contains work for the **Shelter Animal Outcomes** competition on [Kaggle](https://www.kaggle.com/competitions/shelter-animal-outcomes/overview). The goal of this project is to predict the outcome of animals entering shelters using machine learning models. The project leverages **Orange Data Mining**, a powerful and intuitive data mining software for building machine learning workflows.

## Project Overview

The **Shelter Animal Outcomes** dataset includes various features related to the animals’ intake conditions, such as:

- Animal type
- Breed
- Color
- Age
- Date of intake
- Intake condition

The objective is to predict the outcomes for the animals, which can include:

- Adoption
- Transfer
- Euthanasia
- Return to owner
- Death

## Tools and Technologies

- **Orange Data Mining**: Used for building and testing machine learning models through a visual workflow interface.

## Repository Structure

- **data/**: This folder contains the dataset files used for analysis.
- **workflows/**: This folder contains Orange workflows used in the project.
  - `shelter-animal-outcomes.ows`: The primary Orange Data Mining workflow file for this project.
- **results/**: Contains results from model predictions.
- **README.md**: This file, providing an overview of the project.
- **LICENSE**: Project license.

## How to Use

1. Clone the repository:

   ```bash
   git clone https://github.com/edwardnguyen225/orange-shelter-animal-outcomes.git
   ```

2. Install Orange Data Mining from the official [Orange website](https://orangedatamining.com/).
3. Load the dataset into Orange.
4. Use the workflows located in the `workflows/` folder to train and test models.

## Dataset

The dataset used in this project is available on Kaggle. You can download it from the competition page:
[Shelter Animal Outcomes](https://www.kaggle.com/competitions/shelter-animal-outcomes/data).

Make sure to place the dataset in the `data/` folder for proper workflow execution.

## Next Steps

- Improve the prediction accuracy by experimenting with different Orange widgets and machine learning models.
- Perform feature engineering and data preprocessing within Orange to enhance the model.

## Contributions

Contributions are welcome! If you have suggestions or would like to add features, feel free to create a pull request or open an issue.
