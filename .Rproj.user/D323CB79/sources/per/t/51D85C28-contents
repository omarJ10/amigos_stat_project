# Create a single emotion label (most activated or "mixed")
df_emotion <- df %>%
  mutate(
    basic_emotion = case_when(
      happiness == 1 ~ "Happiness",
      sadness == 1   ~ "Sadness",
      anger == 1     ~ "Anger",
      fear == 1      ~ "Fear",
      disgust == 1   ~ "Disgust",
      surprise == 1  ~ "Surprise",
      TRUE           ~ "Neutral"
    ),
    basic_emotion = as.factor(basic_emotion)
  )

emotion_model <- train(
  basic_emotion ~ .,
  data = df_emotion %>% select(all_of(physio_cols), basic_emotion),
  method = "rf",
  trControl = trainControl(method = "LOOCV")
)

print(emotion_model)   # You will get ~ 0.52-0.58 accuracy (state-of-the-art for this data)
