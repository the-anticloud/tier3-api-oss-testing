# Developer Cookbook — api-oss-testing
**Stack:** Python 3.11, pytest, hypothesis (property-based), atheris (fuzzing), AIOSS_FORMAT
**Domain:** Sovereign test framework: property-based, fuzz, and integration testing for Anticloud
**License:** Apache-2.0 | **IP:** USPTO pending 2026, Anticloud FZ LLE

## Core Usage

```python
from api_oss_testing import TestRunner
runner = TestRunner(aioss_chain='./tests.aioss')

# Generate tests with PAX
tests = runner.generate_tests(
    target='aioss_format.AIOSSChain.append',
    pax_model='./pax-27b-q4.gguf',
    n_cases=20
)
tests.write('./tests/test_aioss_generated.py')

# Run with AIOSS audit
result = runner.run('./tests/', coverage=True)
print(f'Pass: {result.passed}, Fail: {result.failed}, Coverage: {result.coverage:.1%}')
```

## AIOSS Chain Append

```python
import hashlib, time

def aioss_append(chain_path, payload: bytes, module_id: str):
    entry_hash = hashlib.sha3_256(payload).digest()
    ts = int(time.time_ns()).to_bytes(8, 'big')
    with open(chain_path, 'rb') as f:
        f.seek(-32, 2); prev_hash = f.read(32)
    new_hash = hashlib.sha3_256(prev_hash + entry_hash + ts).digest()
    with open(chain_path, 'ab') as f:
        f.write(ts + entry_hash + new_hash)
    return new_hash.hex()

# After every api-oss-testing output:
chain_hash = aioss_append("./api_oss_testing.aioss",
                           result_bytes, "api-oss-testing")
```

## Performance & Integration

Performance: profile with api-oss-devtools. Benchmark with api-oss-analytics. Integration: all api-oss-testing operations are logged to api-oss-logging and audited by api-oss-compliance.
