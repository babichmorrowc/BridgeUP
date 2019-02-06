# BridgeUP
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
hyades_df = pd.read_csv("oh_table.csv")
hyades_df.head()
g = hyades_df["G"].loc[hyades_df["group_id"]== 2]
j = hyades_df["J"].loc[hyades_df["group_id"]== 2]
d = hyades_df["distance"].loc[hyades_df["group_id"]== 2]
absmag = g - 5 * np.log10(d) + 5
x = g - j
cm = plt.cm.get_cmap("RdYlBu_r")
SunJ= 3.64
SunG = 5.12
SX = SunG - SunJ
plt.scatter(SX, SunG, color= "gold", marker = "*", s = 200 )
plt.scatter(x, absmag, c = x, cmap= cm)
plt.gca().invert_yaxis()
plt.title("Hyades")
plt.xlabel("Color (G-J)")
plt.ylabel("Absolute Magnitude (G)")
plt.show()
plt.hist(absmag, bins = 10)
plt.show()
