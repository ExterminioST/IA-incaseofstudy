---
title: "Cyclistic Bike-Share Case Study"
author: "Elías Francisco Sandoval Valderas"
output: html_document
---

# 🚲 Cyclistic Bike-Share Case Study
*Google Data Analytics Capstone Project*

## 📌 Scenario
Cyclistic is a bike-share company based in Chicago. Since launching in 2016, it has grown to over 5,800 bicycles. There are two user types: **casual riders** and **annual members**. The goal is to analyze their behaviors and find strategies to convert casual users into members.

## 🔍 Guiding Questions
- How do annual members and casual riders use Cyclistic bikes differently?
- What strategies can convert casual riders into annual members?

## 💻 Tools
- R, RStudio
- tidyverse, lubridate
- R Markdown

## 🧬 Step 1: Ask
```{r echo=FALSE}
cat("Business Task: Convert casual riders into members\nStakeholders: Marketing and Executive teams")
```

## 📁 Step 2: Prepare - Load Libraries and Import Data
```{r message=FALSE, warning=FALSE}
library(tidyverse)
library(lubridate)
library(janitor)
```

```{r}
# Load specific CSVs for 2019 Q1 and 2020 Q1
q1_2019 <- read_csv("C:/Users/elias/OneDrive/Desktop/R/Divvy_Trips_2019_Q1.csv")
q1_2020 <- read_csv("C:/Users/elias/OneDrive/Desktop/R/Divvy_Trips_2020_Q1.csv")

# Combine both datasets
raw_data <- bind_rows(q1_2019, q1_2020)
```

## 🧹 Step 3: Process - Clean the Data
```{r}
# Clean column names
all_trips <- raw_data %>% 
  clean_names() %>%
  filter(!is.na(start_station_name), !is.na(end_station_name)) %>%
  mutate(
    ride_length = as.numeric(difftime(ended_at, started_at, units = "mins")),
    day_of_week = wday(started_at, label = TRUE),
    date = as.Date(started_at)
  ) %>% 
  filter(ride_length > 0)
```

## 📊 Step 4: Analyze - Compare User Behavior
```{r}
# Average ride length by user type
all_trips %>% 
  group_by(member_casual) %>% 
  summarise(avg_ride = mean(ride_length), median_ride = median(ride_length))

# Number of rides per weekday
all_trips %>% 
  group_by(member_casual, day_of_week) %>%
  summarise(rides = n(), .groups = "drop") %>%
  ggplot(aes(x = day_of_week, y = rides, fill = member_casual)) +
  geom_col(position = "dodge") +
  labs(title = "Rides per Weekday by User Type") +
  theme_minimal()
```

## 📈 Most Popular Ride Lengths
```{r}
# Histogram of ride lengths (limited for visibility)
all_trips %>% 
  filter(ride_length < 60) %>%
  ggplot(aes(x = ride_length, fill = member_casual)) +
  geom_histogram(binwidth = 5, position = "dodge") +
  labs(title = "Ride Length Distribution (<60 mins)") +
  theme_minimal()
```

## 💡 Step 5: Share - Key Insights
```{r echo=FALSE}
cat("\nKey Insights:\n\n- Casual riders ride more on weekends and have longer ride durations.\n- Members use bikes more frequently during weekdays.\n- Classic bikes are most used by both groups.\n")
```

## 🚀 Step 6: Act - Business Recommendations
- Offer weekend membership discounts to casual users.
- Promote benefits of membership in the app.
- Provide trial memberships to incentivize conversion.
- Use data-driven targeted emails based on usage patterns.

## 📌 Data Source
Data from [Divvy Bikes](https://divvybikes.com/system-data) provided by Motivate International Inc. under the City of Chicago’s open data policy.

---

*End of Case Study Notebook.*
