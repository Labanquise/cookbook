# Appel des fichiers externes

```html
// Some code
  {{ $poppins := resources.Get "/fonts/poppins.woff2" }}
  {{ $poppinsBold := resources.Get "/fonts/poppins-bold.woff2" }}
  {{ $indieflower := resources.Get "/fonts/indieflower.woff2" }}
  {{ $lobster := resources.Get "/fonts/lobster.woff2" }}
  {{ $material := resources.Get "/fonts/material.woff2" }}
  <link rel="preload" as="font" href="{{ $poppins.Permalink }}" type="font/woff2" crossorigin>
  <link rel="preload" as="font" href="{{ $poppinsBold.Permalink }}" type="font/woff2" crossorigin>
  <link rel="preload" as="font" href="{{ $indieflower.Permalink }}" type="font/woff2" crossorigin>
  <link rel="preload" as="font" href="{{ $lobster.Permalink }}" type="font/woff2" crossorigin>
  <link rel="preload" as="font" href="{{ $material.Permalink }}" type="font/woff2" crossorigin>
```
