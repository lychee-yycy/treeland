pkg_search_module(WLROOTS REQUIRED IMPORTED_TARGET wlroots)

add_library(treeland-protocols STATIC)

target_sources(treeland-protocols PUBLIC
FILE_SET HEADERS
FILES
    ext_foreign_toplevel_list_impl.h
    foreigntoplevelhandlev1.h
    foreign_toplevel_manager_impl.h
    output_manager_impl.h
    personalization_manager_impl.h
    personalizationmanager.h
    shortcut_manager_impl.h
    utils.h
    qshortcutmanager.h
)

target_sources(treeland-protocols PRIVATE
    foreign_toplevel_manager_impl.cpp
    shortcut_manager_impl.cpp
    ext_foreign_toplevel_list_impl.cpp
    foreigntoplevelhandlev1.cpp
    foreigntoplevelmanagerv1.cpp
    output_manager_impl.cpp
    personalization_manager_impl.cpp
    personalizationwindowcontext.cpp
    personalizationwallpapercontext.cpp
    personalizationmanager.cpp
    qshortcutmanager.cpp
    dockpreviewcontextv1.cpp
)

target_compile_definitions(treeland-protocols
    PRIVATE
    WLR_USE_UNSTABLE
)

target_link_libraries(treeland-protocols
    PUBLIC
        treeland
        treeland-data
        treeland-quick-protocols
        PkgConfig::WLROOTS
        Waylib::WaylibServer
        Qt${QT_MAJOR_VERSION}::Core
        Qt${QT_MAJOR_VERSION}::Gui
        Qt${QT_MAJOR_VERSION}::Quick
)
