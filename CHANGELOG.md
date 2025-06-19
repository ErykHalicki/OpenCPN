# CHANGELOG

## [Custom GPX Extensions Implementation] - 2025-06-19

### Added
- **Custom GPX Extensions Preservation**: Implemented functionality to preserve and maintain custom XML extensions in GPX files throughout the OpenCPN workflow (load → database → export cycle)

### Modified Files

#### `model/include/model/route_point.h`
- Added `SetCustomExtensions()` method with error handling (lines 165-178)
- Added `pugi::xml_document m_customExtensions` member (line 628)

#### `model/src/navobj_db.cpp`
- Added `custom_extensions` TEXT column to database schema with ALTER TABLE logic (lines 603-640)
- Enhanced `LoadAllRoutes()` function to load custom extensions from database (lines 1583-1909)
- Implemented backward compatibility for existing database files

#### `model/src/nav_object_database.cpp`
- Enhanced `GPXCreateWpt()` function to export custom extensions to GPX (lines 833-850)
- Added XML node copying from RoutePoint to GPX output

### Technical Implementation
- Uses pugi::xml library for XML document handling
- Deep copying of XML nodes to preserve extension structure
- Comprehensive try-catch blocks for XML operations
- Safe ALTER TABLE operations with column existence checking

### Impact
- Routes with custom GPX extensions now fully preserved through save/load cycles
- Maintains backward compatibility with existing OpenCPN installations
- Enhanced error handling for XML processing operations