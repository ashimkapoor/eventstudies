# eventstudies

An R package for conducting event studies and a platform for
methodological research on event studies. 

## Installation

### Stable version
**Release notes**: https://github.com/nipfpmf/eventstudies/releases/tag/v1.2
```R
devtools::install_github("nipfpmf/eventstudies", ref="master")
```

### Latest version which has an argument for the estimation period
```R
devtools::install_github("ashimkapoor/eventstudies", ref="setting-estimation-period")
```

## Usage

```R
library(eventstudies)
data(OtherReturns)
data(StockPriceReturns)
data(SplitDates)
es.mm <- eventstudy(firm.returns = StockPriceReturns,
# This is where the new argument is being used.
 estimation.period = c(-300,-10),
 event.list = SplitDates,
 event.window = 5,
 type = "marketModel",
 to.remap = TRUE,
 remap = "cumsum",
 inference = TRUE,
 inference.strategy = "bootstrap",
 model.args = list(market.returns=OtherReturns$NiftyIndex)
 )

plot(es.mm)

es.mm1 <- eventstudy(firm.returns = StockPriceReturns,
# New argument being used.
 estimation.period = c(-30,-10),
 event.list = SplitDates,
 event.window = 5,
 type = "marketModel",
 to.remap = TRUE,
 remap = "cumsum",
 inference = TRUE,
 inference.strategy = "bootstrap",
 model.args = list(market.returns=OtherReturns$NiftyIndex)
 )

plot(es.mm1)
```

## Help
```R
?eventstudy
```


## License

GPL-2

