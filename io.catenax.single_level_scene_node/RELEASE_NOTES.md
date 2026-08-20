# Changelog
All notable changes to this model will be documented in this file.

## [Unreleased]
### Added
- `BoundingVolumeAbstractEntity` with a shared `boundingVolumeType` property (Enumeration: "AABB" for axis-aligned bounding box, "OBB" for oriented bounding box), disambiguating how any bounding volume was derived.
- `BoundingSphere` entity (extends `BoundingVolumeAbstractEntity`, `diameter` property), so a sphere representation now carries the same type disambiguation as a box.
- `referenceCoordinateSystem` property on `BoundingVolumeAbstractEntity` (reuses the existing `localTransform`/`MatrixTransform` shape) giving an oriented bounding box (OBB) entry its own origin and orientation. Absent means the volume is expressed directly in the node's own `localTransform` frame, i.e. an axis-aligned bounding box (AABB).
- `minPoint`/`maxPoint`/`length`/`width`/`height`/`diameter` descriptions clarified: always expressed in the volume's own frame (`referenceCoordinateSystem` if present, else the node's `localTransform`), so they never need rotation applied to be read directly — e.g. `length`/`width`/`height` are usable as-is for a machining stock-size calculation regardless of AABB or OBB.

### Changed
- `boundingVolume` renamed to `boundingVolumes` and changed from a single `BoundingBox` to a polymorphic set of `BoundingVolumeAbstractEntity` (`BoundingBox` or `BoundingSphere`), so multiple representations (e.g. one AABB, one OBB) can be given in parallel.
- `BoundingBox` now extends `BoundingVolumeAbstractEntity` instead of declaring its own type property directly.
- `BoundingVolumeType` enum values changed from ad hoc strings ("relative to coordinate system", "best fit") to standard AABB/OBB terminology, grounded in how USD (`GfBBox3d`), IFC (`IfcBoundingBox`), and STEP (`box_domain`) represent bounding volumes.

### Removed
- Standalone `boundingSphere` property (a bare diameter float) — folded into the new `BoundingSphere` entity inside `boundingVolumes`.

## [1.0.0] - 2025-10-08
### Added
- initial version of model

### Changed
n/a

### Removed
n/a
