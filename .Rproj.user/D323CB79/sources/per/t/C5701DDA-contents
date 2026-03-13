# Valence/Arousal distribution by video type
p1 <- ggplot(df, aes(x = valence, fill = video_type)) +
  geom_density(alpha = 0.6) +
  theme_minimal() + labs(title = "Valence distribution")

p2 <- ggplot(df, aes(x = arousal, fill = video_type)) +
  geom_density(alpha = 0.6) +
  theme_minimal() + labs(title = "Arousal distribution")

p1 + p2

# Boxplots - you will clearly see social context in long videos
ggplot(df, aes(x = video_type, y = valence, fill = video_type)) +
  geom_boxplot() + theme_minimal() + labs(title = "Valence by Social Context")

ggplot(df, aes(x = video_type, y = arousal, fill = video_type)) +
  geom_boxplot() + theme_minimal() + labs(title = "Arousal by Social Context")
