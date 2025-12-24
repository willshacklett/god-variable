import numpy as np

def langevin(T=1000, dt=0.01, D=0.5, lam=0.0, seed=0):
    np.random.seed(seed)
    x = np.zeros(T)
    for t in range(1, T):
        noise = np.sqrt(2*D*dt) * np.random.randn()
        phi_grad = lam * x[t-1]  # stabilizing proxy
        x[t] = x[t-1] - phi_grad*dt + noise
    return x
