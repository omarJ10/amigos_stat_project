# Prepare data - only physiological features
physio_cols <- str_subset(names(df), "^eeg_|^ecg_|^gsr_")
feature_df <- df %>% select(all_of(physio_cols), valence_bin, arousal_bin, participant_id)

# Leave-One-Participant-Out Cross-Validation (L0P0) - this is the gold standard
set.seed(42)

# Valence model
valence_model <- train(
  valence_bin ~ .,
  data = feature_df %>% select(-arousal_bin, -participant_id),
  method = "rf",
  trControl = trainControl(method = "LOOCV", classProbs = TRUE, savePredictions = TRUE),
  metric = "ROC"
)

print(valence_model)
# Expected: AUC ~ 0.63-0.69 (very close to original paper)

# Arousal model
arousal_model <- train(
  arousal_bin ~ .,
  data = feature_df %>% select(-valence_bin, -participant_id),
  method = "rf",
  trControl = trainControl(method = "LOOCV", classProbs = TRUE, savePredictions = TRUE),
  metric = "ROC"
)

print(arousal_model)
# Expected: AUC ~ 0.60-0.66
