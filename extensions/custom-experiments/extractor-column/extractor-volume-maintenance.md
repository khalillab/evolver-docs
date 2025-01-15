# Extractor Volume Maintenance

## Maintaining the Solvent Layer

The solvent layer on top of the cells / media in the extractor must be maintained. However, in the basic eVOLVER setup, volume in the vial is maintained by setting the efflux straw's height to a certain vial volume and pumping any excess volume away. Therefore in basic eVOLVER, the solvent layer would be the first to go.

Instead, the extractor controls the volume in the vial by using the `od90` photodiode - LED pair to monitor fluid levels.

## Volume Maintenance Algorithm

1. **Experiment started**
2.  **Pump Wait**: No pumping until `vol_check_wait` is exceeded

    ```python
    vol_check_wait = 0.15 # (hours) time to wait before regulating extractor volume
    ```
3. **Blanking**: the value where the volume line is below the volume sensor is taken
   1. The raw `od90` values just before `vol_check_wait` are stored and averaged to use as this threshold 'blank'
4. **Continuous Pumping**: Cells are pumped from the cell growth bioreactor (chemostat or turbidostat) to the extractor and back from the extractor to the cell growth bioreactor
   1. In cycles based on the eVOLVER [broadcast timing](../../../software/server-raspberry-pi/)
5. **Pump Duration Biasing**: Pumping out from the extractor is shorter than pumping in
6. **Extractor Volume Increases**: The volume in the extractor steadily rises towards the volume sensor
7. **Volume Threshold Exceeded**: When the volume line increases above threshold, the system will only pump OUT one broadcast cycle, decreasing the volume level
8. **Steps repeat**
