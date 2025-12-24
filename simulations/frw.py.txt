import numpy as np

def frw(t, rho0=1.0, lam=0.0):
    a = np.ones_like(t)
    for i in range(1, len(t)):
        H2 = rho0/(a[i-1]**3) + lam*(1.0/(1+t[i]**2))
        a[i] = a[i-1] * np.exp(np.sqrt(H2)*(t[i]-t[i-1]))
    return a
