# Changelog
All notable changes to this model will be documented in this file.

## [Unreleased]
### Added
n/a

### Changed
n/a

### Removed
- `boundingBox` / `boundingSphere` properties (and their `BoundingBoxEntity`, `BoundingBoxCharacteristic`, `BoundingSphereCharacteristic`, length/width/height sub-properties) from `GeometryDataEntity` — bounding volume representations now live exclusively in `io.catenax.single_level_scene_node` to avoid two divergent definitions of the same concept.

## [1.0.0] - 2025-07-31
### Added
- initial version of model

### Changed
n/a

### Removed
n/a
