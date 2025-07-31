# CSS break-before property outside print media
Created: 7/31/2025, 1:38:09 PM
Last Updated: 7/31/2025, 1:38:09 PM
---

### User

does the css property break-before have any meaning outside of the print media ?


---

### Assistant (kimi-k2)

Yes.  
`break-before` (and its siblings `break-after`, `break-inside`) are **not** limited to print.  
They are defined in the CSS Fragmentation spec and apply whenever the layout engine has to fragment a box across **fragmentainers**—pages, columns, or regions.

- `break-before: page` – forces a **page** break (print, or paged media such as `overflow: paged-x`).  
- `break-before: column` – forces a **column** break inside multi-column containers (`column-count`, `column-width`).  
- `break-before: region` – forces a break between CSS Regions (deprecated, but still implemented in some browsers).  
- `break-before: avoid` / `avoid-page` / `avoid-column` – tries to avoid the corresponding break.

So in a multi-column layout on screen, `break-before: column` is fully honored; in a paged screen context (e.g., PrinceXML, WeasyPrint, or Chromium’s “overflow: paged-x” prototype) `break-before: page` works as well.


---
