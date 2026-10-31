# IEE2714 — Tarea 3: filtrado notch y deconvolución regularizada

Todo el código está en el notebook `Tarea3_IEE2714.ipynb`. Al ejecutarlo de principio a fin se
reproducen **todas** las figuras y tablas del informe (`Tarea3_IEE2714.pdf`).

## Estructura

```
Tarea3_IEE2714.ipynb   código + experimentos (Pregunta 1, Bonus y Pregunta 2)
data/
  P1.CR2               imagen RAW con ruido periódico (Pregunta 1)
  cameraman.jpg        imagen ideal x (Pregunta 2)
  psf.png              PSF h de 15x15 (Pregunta 2)
figs/                  figuras generadas (mismos nombres que en el informe)
resultados/            imagen en gris de P1 (caché) e imagen filtrada final
```

## Requisitos

Python ≥ 3.10 y:

```
pip install numpy scipy matplotlib pillow rawpy jupyter
```

`rawpy` (LibRaw) se usa sólo para leer el mosaico de Bayer del archivo `.CR2`. Si no está
instalado, el notebook intenta usar la biblioteca de sistema `libraw` mediante `ctypes`
(por ejemplo, `sudo apt install libraw-dev` en Ubuntu/Debian).

## Ejecución

```
jupyter notebook Tarea3_IEE2714.ipynb      # y luego "Run All"
# o bien, sin abrir la interfaz:
jupyter nbconvert --to notebook --execute --inplace Tarea3_IEE2714.ipynb
```

Tiempo aproximado: 8–10 minutos (la imagen RAW es de 2856×4290 píxeles).
La primera ejecución guarda la imagen en gris en `resultados/P1_gris.npy`; las siguientes la reutilizan.

## Parámetros principales (configurables en el notebook)

| Parámetro | Valor usado | Dónde |
|---|---|---|
| Centros de los notch (c/px) | (0, 0.25) y (0.5, 0.25) + simétricos | `NOTCH_CENTROS` |
| Familia y ancho final | Gaussiano, σ = 1e-3 c/px | `TIPO_FINAL`, `ANCHO_FINAL` |
| Padding | reflexión, p = 64 px, tamaño múltiplo de 4 | `PAD_MODO`, `PAD_P`, `PAD_MULT` |
| Ruido P2 | σ_n ∈ {0.01, 0.05}, semilla 2026 | `SIGMAS_N` |
| Barrido de K (Wiener) | 71 valores en [1e-7, 1] (log) | `KS` |
| Tikhonov GD | λ ∈ {0, K*/10, K*, 10K*, 100K*}, τ ∈ {0.5, 1.9, 2.05} | `LAMS`, `TAUS` |

Sólo se usan FFT/IFFT (`scipy.fft`), operaciones de arreglos (NumPy), lectura de archivos y
visualización. Los filtros notch, Wiener, Tikhonov y el descenso de gradiente están
implementados a mano.





