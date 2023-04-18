# String down time production losses

String availability losses are calculated based on string availability for plant as described in chapter 5.3.4, but only availability during midday hours are used for the entire day.
- Production Loss Strings = E_meas * (1-SA_midday) / SA_midday

Factors calculated as follows:
- E_meas: measured actual production for plant (see 5.1.1)
- SA_midday: String availability (0-1) for plant during midday 10-14 hours
