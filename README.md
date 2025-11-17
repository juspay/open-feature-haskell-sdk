# OpenFeature Haskell SDK

[![Specification](https://img.shields.io/static/v1?label=Specification&message=v0.8.0&color=yellow)](https://openfeature.dev/specification/versions/v0.8.0)
[![a](https://img.shields.io/badge/slack-%40cncf%2Fopenfeature-brightgreen.svg?logo=slack)](https://cloud-native.slack.com/archives/C0344AANLA1)

> **⚠️ WARNING: This SDK is a work in progress.**
>
> The OpenFeature Haskell SDK is in early development. The API may change, and many features are not yet implemented. The package has not been published to Hackage yet.

## Introduction

[OpenFeature](https://openfeature.dev) is an open specification that provides a vendor-agnostic, community-driven API for feature flagging that works with your favorite feature flag management tool.

## Quick Start

### Usage

```haskell
import Data.OpenFeature.Api
import Data.OpenFeature.Client
import Data.OpenFeature.EvaluationContext

main :: IO ()
main = do
  -- Set a provider
  setDefaultProvider myProvider
  
  -- Create a client
  client <- createClient
  
  -- Evaluate a flag with context
  let ctx = contextWithTargetingKey "user-123"
  result <- getBoolValue client "my-feature" (Just ctx)
  
  case result of
    Right flagValue -> print flagValue
    Left err -> print err
```

### Implementing a Provider

Implement the `FeatureProvider` typeclass to integrate with any feature flag backend. See `Data.OpenFeature.FeatureProvider` for the interface definition.

## Features

| Status | Feature | Description |
|--------|---------|-------------|
| ✅ | Providers | Integrate with a feature flag provider |
| ✅ | Targeting | Context-aware flag evaluation |
| ✅ | Evaluation API | Flag evaluation with typed values |
| ✅ | Evaluation Context | Contextual data for flag evaluation |
| ✅ | Client | Named clients with isolated contexts |
| ❌ | Hooks | Lifecycle hooks for flag evaluation |
| ❌ | Events | Provider lifecycle events |
| ❌ | Logging | Structured logging integration |

## License

BSD-3-Clause
