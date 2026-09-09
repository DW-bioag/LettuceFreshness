# Lettuce Freshness under Varying Illumination

This repository contains the image and human sensory-evaluation data associated with:

> D. Wang, S. Sethu, S. Nathan, Z. Li, V. J. Hogan, C. Ni, S. Zhang, and H.-S. Seo, “Is human perception reliable? Toward illumination robust food freshness prediction from food appearance—Taking lettuce freshness evaluation as an example,” *Journal of Food Engineering*, vol. 381, article 112179, 2024. [https://doi.org/10.1016/j.jfoodeng.2024.112179](https://doi.org/10.1016/j.jfoodeng.2024.112179)

The study investigates how illumination color temperature and power affect human and machine perception of lettuce freshness. Please consult the [published paper](https://www.sciencedirect.com/science/article/pii/S0260877424002450) for the experimental protocol, statistical analysis, and model results.

![Example image of lettuce sample 1 on day 0 under 3500 K, 17.5 W illumination](image/sample%201/day0/t5s1day0_3500K_17.5W.png)

## Dataset summary

The current dataset is a complete factorial collection of:

| Dimension | Values | Count |
| --- | --- | ---: |
| Lettuce sample | `1`–`9` | 9 |
| Storage day | `0`, `1`, `3`, `5`, `8` | 5 |
| Illumination color temperature | `3500`, `4000`, `4250`, `4500`, `4750` K | 5 |
| Illumination power | `17.5`, `20`, `22.5` W | 3 |

This gives `9 × 5 × 5 × 3 = 675` images. All images are RGB PNG files at 1920 × 1200 pixels. The image directory is approximately 1.5 GB.

`HumanGrade.xlsx` contains one worksheet, `Total`, with 60,075 sensory-evaluation records: 89 panelists × 675 images. Each panelist–image combination occurs exactly once, and the `Sample` values match the 675 image basenames.

## Repository layout

```text
LettuceFreshness/
├── HumanGrade.xlsx
├── image/
│   ├── sample 1/
│   │   ├── day0/
│   │   ├── day1/
│   │   ├── day3/
│   │   ├── day5/
│   │   └── day8/
│   └── ...
└── README.md
```

Each image belongs in `image/sample <sample_id>/day<storage_day>/`.

## Image naming convention

Image filenames follow this pattern:

```text
t5s<sample_id>day<storage_day>_<color_temperature>K_<power>W.png
```

For example:

```text
t5s4day3_4000K_22.5W.png
```

means sample 4, storage day 3, photographed at a color temperature of 4000 K and illumination power of 22.5 W. `t5` is a fixed prefix in the current release and should be preserved unless a future release defines another acquisition identifier.

The `Sample` column in `HumanGrade.xlsx` stores the corresponding filename without the `.png` extension.

## Sensory-evaluation workbook

### `Total` sheet

| Column | Description |
| --- | --- |
| `Set` | Sample set number (`1`–`9`); matches the sample identifier encoded in `Sample`. |
| `Serving_Order` | Recorded presentation-order index (`1`–`75`) within a set. |
| `Sample` | Image identifier and filename stem. |
| `Panel_ID` | Pseudonymous panelist identifier. |
| `Purchase_Intent` | Purchase-intent score on the recorded 0–100 scale. |
| `Overall_Liking` | Overall-liking score on the recorded 0–100 scale. |
| `Freshness` | Perceived-freshness score on the recorded 0–100 scale. |


## Citation

If you use this dataset, cite the associated paper:

```bibtex
@article{wang2024lettucefreshness,
  title   = {Is human perception reliable? Toward illumination robust food freshness prediction from food appearance---Taking lettuce freshness evaluation as an example},
  author  = {Wang, Dongyi and Sethu, Swarna and Nathan, Sabari and Li, Zhenye and Hogan, Victoria J. and Ni, Chao and Zhang, Shengfan and Seo, Han-Seok},
  journal = {Journal of Food Engineering},
  volume  = {381},
  pages   = {112179},
  year    = {2024},
  doi     = {10.1016/j.jfoodeng.2024.112179}
}
```

## License

No license is currently included in this repository. Please contact the dataset authors for reuse terms, and add a `LICENSE` file before distributing the dataset under a specific license.
