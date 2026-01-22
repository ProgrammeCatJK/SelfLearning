# Buy the dip evaluation
---
## Goal
Evaluate whether “Buy the Drip” strategy would outperforms the buy and hold using historical data

## Logic Layer
- Data layer - Data labeling, normalisation and prepare
- Feature layer - turn price into indicators
- ML Layer - learn which indicator matter for reversal
- Strategy and evaluation layer - trade, evaluate, compare
---
### Data Layer
**purpose**: Set time frame, prepare data for ML and random forest in the form of a csv file

Training data: Dec 2022 - April 2025
Validation data: April 2025 - Aug 2025
Testing data: Sep 2025 - Jan 2026

### Feature Layer
Picking which indicator/data are the most relevant to reversal
Indictor
EMA 20, EMA 50, EMA 100, SMA 20, SMA 50, SMA 100, RSI
Normalise features
Dip distance
Define what is reversal and dip 
“Does price rebound by X% within T days?”
### ML Layer


### Evaluation


## Stock Category
- High vol
- Low vol
- Small/Medium/Large cap
- ETF/Bitcoin

##

