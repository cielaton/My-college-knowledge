| Rectifier parameter             | Half-wave rectifier                     | Full-wave rectifier                                               | Full-wave bridge rectifier                                   |
| ------------------------------- | --------------------------------------- | ----------------------------------------------------------------- | ------------------------------------------------------------ |
| Filter capacitor                | $$C=\frac{V_P-V_{on}}{V_r}\frac{T}{R}$$ | $$C=\frac{V_P-V_{on}}{V_r}\frac{T}{2R}$$                          | $$C=\frac{V_P-2V_{on}}{V_r}\frac{T}{2R}$$                    |
| PIV rating                      | $2V_P$                                  | $2V_P$                                                            | $V_P$                                                        |
| Peak diode current(const $V_r$) | Highest ($I_P$)                         | Reduced ($\frac{I_P}{2}$)                                         | Reduced ($\frac{I_P}{2}$)                                    |
| Surge current                   | Highest                                 | Reduced ($\alpha C$)                                              | Reduced ($\alpha C$)                                         |
| Comments                        | Less complexity                         | Smaller capacitor, requires center-tapped transformer, Two diodes | Smaller capacitor, four diodes, no center tap on transformer |

