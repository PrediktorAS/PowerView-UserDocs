# String down time production losses

String losses are calculated in two ways:
- String losses per plant
- String losses per string set (channel)

## String losses per plant
String availability losses are calculated based on string availability for plant as described in chapter 5.3.4, but only availability during midday hours are used for the entire day.
- Production Loss Strings = [Actual Production](../../Yield%20and%20Weather/Actual%20Production/Actual%20Production.md) * (1 - SA_midday) / SA_midday
    - SA_midday: String availability (0-1) for plant during midday 10-14 hours

## String losses per string set (channel)
