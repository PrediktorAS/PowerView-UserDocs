# Tracker down time production losses

Following algorithm is implemented in SCADA to estimate production loss on trackers:
- Production Loss Trackers = E_meas *(1 – TA_ForProdLoss) * (TF - 1)

Factors calculated as follows:
- E_meas: measured actual production for plant
- TAprodloss: Tracker availability (0-1) for plant taking into account available power on tracker for the time period. Removing power due to unavailable strings and inverters
- TF: Transposition Factor = Incline Irradiation / Horizontal Irradiation