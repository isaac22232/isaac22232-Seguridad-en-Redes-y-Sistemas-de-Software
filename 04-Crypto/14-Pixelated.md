### Descripción
I have these 2 images, can you make a flag out of them? [scrambled1.png](https://challenge-files.cylabacademy.net/library/fa686cfe375627b0131e670a19ec4775a873562ee3006dae8a40796e3e2b5e3c/scrambled1.png) [scrambled2.png](https://challenge-files.cylabacademy.net/library/fa686cfe375627b0131e670a19ec4775a873562ee3006dae8a40796e3e2b5e3c/scrambled2.png)

### Solución
```
from PIL import Image
import numpy as np

img1 = Image.open('scrambled1.png')
img2 = Image.open('scrambled2.png')
matriz1 = np.asarray(img1)
matriz2 = np.asarray(img2)

mflag = matriz1 + matriz2

resultado = Image.fromarray(mflag)
resultado.save('flag.png')

print(matriz1)

academy{2f16d0c4}
```

### Notas adicionales


### Referencias
