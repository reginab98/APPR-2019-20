# Obdelava, uvoz in čiščenje podatkov.

Tukaj bomo imeli program, ki bo obdelal, uvozil in očistil podatke (druga faza
projekta).

library(knitr)
library(rvest)
library(gsubfn)
library(tidyr)
library(shiny)
library(readr)

podatki <- read_csv("potniki.csv")
