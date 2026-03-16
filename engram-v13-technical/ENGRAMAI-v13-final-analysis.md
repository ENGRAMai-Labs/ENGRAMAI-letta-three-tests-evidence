# v13 Final Matrix Analysis

## real20_200s_seed700
| lane | accuracy | correct/total | cost_total | cost_per_correct |
|---|---:|---:|---:|---:|
| engram | 0.9882 | 3953/4000 | 9.098 | 0.002302 |
| modern_rag | 0.4695 | 1878/4000 | 4.838 | 0.00257633280085197 |
| rag | 0.6488 | 2595/4000 | 6.832 | 0.0026326836223506743 |
| vector | 0.6515 | 2606/4000 | 7.651 | 0.002935905218726017 |
| naive | 0.5460 | 2184/4000 | 10.904 | 0.004992730769230769 |

Delta vs engram (pp):
- modern_rag: 51.88 pp
- rag: 33.95 pp
- vector: 33.67 pp
- naive: 44.22 pp

## ruler_32k_2000q
| lane | accuracy | correct/total | cost_total | cost_per_correct |
|---|---:|---:|---:|---:|
| engram | 0.9015 | 1803/2000 | 2.68481 | 0.001489079312257349 |
| modern_rag | 0.8240 | 1648/2000 | 1.984273 | 0.001204 |
| rag | 0.7605 | 1521/2000 | 1.988128 | 0.001307 |
| vector | 0.7645 | 1529/2000 | 2.284581 | 0.001494 |
| naive | 0.5500 | 1100/2000 | 3.153351 | 0.002867 |

Delta vs engram (pp):
- modern_rag: 7.75 pp
- rag: 14.10 pp
- vector: 13.70 pp
- naive: 35.15 pp

## babilong_4k_100q
| lane | accuracy | correct/total | cost_total | cost_per_correct |
|---|---:|---:|---:|---:|
| engram | 0.8600 | 86/100 |  |  |
| modern_rag | 0.4700 | 47/100 |  |  |
| rag | 0.4600 | 46/100 |  |  |
| vector | 0.4700 | 47/100 |  |  |
| naive | 0.5800 | 58/100 |  |  |

Delta vs engram (pp):
- modern_rag: 39.00 pp
- rag: 40.00 pp
- vector: 39.00 pp
- naive: 28.00 pp
