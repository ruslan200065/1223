# Yandex SpeechKit for Home Assistant 2026.10+

**Community compatibility build (unofficial)** based on [black-roland/homeassistant-yandex-speechkit](https://github.com/black-roland/homeassistant-yandex-speechkit), including the maintainer's [vendored protobuf 7 branch](https://github.com/black-roland/homeassistant-yandex-speechkit/pull/17).

This variant targets Home Assistant **2026.10+** and avoids the `yandexcloud` SDK's incompatible `protobuf<7` requirement by bundling the SpeechKit v3 gRPC/protobuf stubs. The import from `const.py` is decoupled from protobuf to keep config flow initialization independent of speech SDK imports.

## Install (HACS)

1. Make a Home Assistant backup first.
2. If `black-roland/homeassistant-yandex-speechkit` is installed, remove its HACS repository entry **without deleting the existing HA configuration entry** (or back up `/config/custom_components/yandex_speechkit` before replacing it).
3. HACS -> three dots -> Custom repositories -> enter **https://github.com/ruslan200065/1223** and select **Integration**.
4. Download `Yandex SpeechKit (HA 2026.10+)`, then restart Home Assistant.
5. Confirm the existing `yandex_speechkit` integration and STT/TTS entities load. Keep your existing Yandex Cloud API key; no new key is necessary.

Do **not** install this alongside another custom integration with the same domain `yandex_speechkit`: they would overwrite the same folder. If HACS refuses two sources with the same domain, remove the old custom repository and add this one.

## Scope

- Original integration features preserved: streaming STT, TTS, and optional Yandex.Station TTS proxy.
- No `yandexcloud` dependency; uses Home Assistant core's protobuf 7 / grpcio 1.83.1.
- No Yandex account or Home Assistant instance is available to the maintainer for an end-to-end cloud test. Treat as an experimental compatibility build; check HA logs for exact errors.

## License / attribution

Original integration copyright and license: [MPL-2.0](https://github.com/black-roland/homeassistant-yandex-speechkit/blob/master/LICENSE). SpeechKit gRPC generated sources from [yandex-cloud/cloudapi](https://github.com/yandex-cloud/cloudapi); see vendored `LICENSE` and `VENDOR.txt`. Source changes here remain available under the original license terms.
