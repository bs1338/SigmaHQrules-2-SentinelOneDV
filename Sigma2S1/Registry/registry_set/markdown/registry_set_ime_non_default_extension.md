# registry_set_ime_non_default_extension

## Title
Uncommon Extension In Keyboard Layout IME File Registry Value

## ID
b888e3f2-224d-4435-b00b-9dd66e9ea1f1

## Author
X__Junior (Nextron Systems)

## Date
2023-11-21

## Tags
attack.defense-evasion, attack.t1562.001

## Description
Detects usage of Windows Input Method Editor (IME) keyboard layout feature, which allows an attacker to load a DLL into the process after sending the WM_INPUTLANGCHANGEREQUEST message.
Before doing this, the client needs to register the DLL in a special registry key that is assumed to implement this keyboard layout. This registry key should store a value named "Ime File" with a DLL path.
IMEs are essential for languages that have more characters than can be represented on a standard keyboard, such as Chinese, Japanese, and Korean.


## References
https://www.linkedin.com/pulse/guntior-story-advanced-bootkit-doesnt-rely-windows-disk-baranov-wue8e/

## False Positives
IMEs are essential for languages that have more characters than can be represented on a standard keyboard, such as Chinese, Japanese, and Korean.

## SentinelOne Query
```
ObjectType = "Registry" AND (EndpointOS = "windows" AND ((RegistryKeyPath containsCIS "\Control\Keyboard Layouts\" AND RegistryKeyPath containsCIS "Ime File") AND (NOT RegistryValue endswithCIS ".ime")))

```