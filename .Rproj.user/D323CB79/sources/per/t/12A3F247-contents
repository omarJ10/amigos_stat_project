# 1. Install / load required packages (run once)
if (!require(pacman)) install.packages("pacman")
pacman::p_load(
  tidyverse,    # data wrangling + ggplot2
  caret,        # machine learning
  randomForest, # RF models
  e1071,        # SVM
  pROC,         # AUC + ROC curves
  corrplot,     # correlation plots
  patchwork,     # combine ggplots
  janitor,      # clean column names
  skimr,        # nice summary
  ggcorrplot,   # pretty corr plots
  tidymodels,   # modern ml workflow (optional but recommended)
  readr
)

# 2. Load your data
df <- read_csv("data/AMIGO.csv") %>%
  clean_names() %>%  # makes column names snake_case
  mutate(
    participant_id = as.factor(participant_id),
    video_id       = as.factor(video_id),
    video_type     = as.factor(video_type),
    # Create binary labels exactly like the original AMIGOS paper (median split)
    valence_bin    = as.factor(ifelse(valence > median(valence), "High", "Low")),
    arousal_bin    = as.factor(ifelse(arousal > median(arousal), "High", "Low"))
  )

# Quick look
glimpse(df)
skim(df)
