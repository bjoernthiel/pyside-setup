Changes
=======

1.2.1 (2013-08-16)
------------------

Major changes
~~~~~~~~~~~~~

PySide
******

- In memory qt.conf generation and registration

Shiboken
********

- Better support for more than 9 arguments to methods
- Avoiding a segfault when getting the .name attribute on an enum value with no name

PySide-setup
************

- Switched to the new setuptools (v0.9.8) which has been merged with Distribute again and works for Python 2 and 3 with one codebase
- Support for building windows binaries with only Windows SDK installed (Visual Studio is no more required)
- Removed --msvc-version option. Required msvc compiler version is now resolved from python interpreter version

1.2.0 (2013-07-02)
------------------

Major changes
~~~~~~~~~~~~~

PySide
******

- Fix multiple segfaults and better track the life time of Qt objects
- Fix multiple memory leaks

Shiboken
********

- Install the shiboken module to site-packages
- Fix multiple segfaults

PySide-setup
************

- On Windows system, when installing PySide binary distribution via easy_install,
  there is no more need to call the post-install script
- Support for building windows binaries outside of Visual Studio command prompt
- Build and package the shiboken docs when sphinx is installed

Complete list of changes and bug fixes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

PySide
******

- Set up PYTHONPATH for tests correctly
- Fix potential segfault at shutdown
- Fix PYSIDE-61
- Tell Qt to look for qml imports in the PySide package
- fix build in C++11 mode
- Fix QByteArray memory leak
- Ignore QtCore import errors when initializing plugins folder
- Preload OpenSSL DLLs on Windows.
- Look first in the PySide package for Qt's plugins folder, instead of just in Qt's install or build folder
- Add explicit type conversion to fix mingw compile error
- Use QObject property to invalidate wrapper before deletion
- Invalidate metaObject wrapper before deletion
- Fix reference leak on convertion from a C++ map type to Python dict
- Change the order of pysitetest and signals directories because signals/disconnect_test.py depends on pysidetest module

Shiboken
********

- Removed old logos from html docs
- Add missing return on module init error
- Don't break -Werror=non-virtual-dtor
- Fixing shiboken test for minimal binding test
- Decref reference to type object
- Fix segfault when using shiboken.delete
- Use non-static method def for instance methods
- Fix bug introduced when recursive_invalidate was added
- fix build in C++11 mode
- Prevent infinite recursion in invalidate
- Fix possible conflict with garbage collector
- Fix possible crash at exit
- Fix handling of unsigned long long and provide unittests
- Add test to illustrate issue on typedef enum
- Use getWrapperForQObject to convert if generating for PySide
- Allow compilation without a python shared library
- Use parent class's metaObject if wrapper is NULL
- Optionally assert on free'd pointer with a valid wrapper
- Find python3 libraries when built with pydebug enabled
- Fix PYSIDE-108 bug and add example
- PYSIDE-83 Fix segfault calling shiboken.dump
- Fix and test case for bug PYSIDE-72
- Override all functions with the same name, not just one
- Update vector conversion
- Add typedef examples to minimal
- Add test files back to cmake
- Don't use it->second after erasing it
- Find function modifications defined in the 2nd+ base class. Fixes bug PYSIDE-54.
- Set a default hash function for all ObjectTypes. Fix bug PYSIDE-42.
- Fix compilation when there is no libxslt installed on the system.
- Fixed resolving of SOABI. SOABI is implemented on Linux, but not on Windows
- Don't use inline methods in dllexported classes to keep VC++ happy
- Use SpooledTemporaryFile in 2.6+ os.tmpfile() fails on win32 if process doesn't have admin permissions

PySide-setup
************

- Support for building windows binaries outside of Visual Studio command prompt
- Build and package the shiboken docs when sphinx is installed
- Support Ubuntu 13.04 and Fedora 18
- Fixed "develop" setuptools command
- Documentation updates
- Add --build-tests option to enable building the tests
- Add --jom and --jobs options
- Add --no-examples option to exclude the examples
- Add --relwithdebinfo option to enable a release-with-debug-info build mode
- Add --ignore-git option
- Add --make-spec option to specify make generator

1.1.2 (2012-08-28)
------------------

Bug fixes
~~~~~~~~~

- During signal emission don't get return type after callback
- Invalidate QStandardModel::invisibleRootItem in clear() method
- QAbstractItemModel has wrong ownership policy for selectionModel()
- Improved QVector to python conversion
- Disable docstring generation if tools aren't found.
- Fixed some issues compiling PySide using VC++
- Install the shiboken module to site-packages
- Fix compilation when there is no libxslt installed on the system.
- Set a default hash function for all ObjectTypes.
- Fix segfault calling shiboken.dump

1.1.1 (2012-04-19)
------------------

Major changes
~~~~~~~~~~~~~

- Unified toolchain! No more GeneratorRunner and ApiExtractor, now you just need Shiboken to compile PySide.

Bug fixes
~~~~~~~~~

- 1105 Spyder fails with HEAD
- 1126 Segfault when exception is raised in signalInstanceDisconnect
- 1135 SIGSEGV when loading custom widget using QUiLoader when overriding createWidget()
- 1041 QAbstractItemModel has wrong ownership policy for selectionModel()
- 1086 generatorrunner segfault processing #include
- 1110 Concurrency error causes GC heap corruption
- 1113 Instantiating QObject in user-defined QML element's constructor crashes if instantiated from QML
- 1129 Segmentation fault on close by QStandardItem/QStandardItemModel
- 1104 QSettings has problems with long integers
- 1108 tests/QtGui/pyside_reload_test.py fails when bytecode writing is disabled
- 1138 Subclassing of QUiLoader leads to "Internal C++ object already deleted" exception (again)
- 1124 QPainter.drawPixmapFragments should take a list as first argument
- 1065 Invalid example in QFileDialog documentation
- 1092 shiboken names itself a 'generator'
- 1094 shiboken doesn't complain about invalid options
- 1044 Incorrect call to parent constructor in example
- 1139 Crash at exit due to thread state (tstate) being NULL
- PYSIDE-41 QModelIndex unhashable

1.1.0 (2012-01-02)
------------------

Major changes
~~~~~~~~~~~~~

- New type converter scheme

Bug fixes
~~~~~~~~~

- 1010 Shiboken Cygwin patch
- 1034 Error compiling PySide with Python 3.2.2 32bit on Windows
- 1040 pyside-uic overwriting attributes before they are being used
- 1053 pyside-lupdate used with .pro files can't handle Windows paths that contain spaces
- 1060 Subclassing of QUiLoader leads to "Internal C++ object already deleted" exception
- 1063 Bug writing to files using "QTextStream + QFile + QTextEdit" on Linux
- 1069 QtCore.QDataStream silently fails on writing Python string
- 1077 Application exit crash when call QSyntaxHighlighter.document()
- 1082 OSX binary links are broken
- 1083 winId returns a PyCObject making it impossible to compare two winIds
- 1084 Crash (segfault) when writing unicode string on socket
- 1091 PixmapFragment and drawPixmapFragments are not bound
- 1095 No examples for shiboken tutorial
- 1097 QtGui.QShortcut.setKey requires QKeySequence
- 1101 Report invalid function signatures in typesystem
- 902 Expose Shiboken functionality through a Python module
- 969 viewOptions of QAbstractItemView error

1.0.9 (2011-11-29)
------------------

Bug fixes
~~~~~~~~~

- 1058 Strange code in PySide/QtUiTools/glue/plugins.h
- 1057 valgrind detected "Conditional jump or move depends on uninitialised value"
- 1052 PySideConfig.cmake contains an infinite loop due to missing default for SHIBOKEN_PYTHON_SUFFIX
- 1048 QGridLayout.itemAtPosition() crashes when it should return None
- 1037 shiboken fails to build against python 3.2 (both normal and -dbg) on i386 (and others)
- 1036 Qt.KeyboardModifiers always evaluates to zero
- 1033 QDialog.DialogCode instances and return value from \QDialog.exec_ hash to different values
- 1031 QState.parentState() or QState.machine() causes python crash at exit
- 1029 qmlRegisterType Fails to Increase the Ref Count
- 1028 QWidget winId missing
- 1016 Calling of Q_INVOKABLE method returning not QVariant is impossible...
- 1013 connect to QSqlTableModel.primeInsert() causes crash
- 1012 FTBFS with hardening flags enabled
- 1011 PySide Cygwin patch
- 1010 Shiboken Cygwin patch
- 1009 GeneratorRunner Cygwin patch
- 1008 ApiExtractor Cygwin patch
- 891 ApiExtractor doesn't support doxygen as backend to doc generation.

1.0.8 (2011-10-21)
------------------

Major changes
~~~~~~~~~~~~~

- Experimental Python3.2 support
- Qt4.8 beta support

Bug fixes
~~~~~~~~~

- 1022 RuntimeError: maximum recursion depth exceeded while getting the str of an object
- 1019 Overriding QWidget.show or QWidget.hide do not work
- 944 Segfault on QIcon(None).pixmap()

1.0.7 (2011-09-21)
------------------

Bug fixes
~~~~~~~~~

- 996 Missing dependencies for QtWebKit in buildscripts for Fedora
- 986 Documentation links
- 985 Provide versioned pyside-docs zip file to help packagers
- 981 QSettings docs should empathize the behavior changes of value() on different platforms
- 902 Expose Shiboken functionality through a Python module
- 997 QDeclarativePropertyMap doesn't work.
- 994 QIODevice.readData must use qmemcpy instead of qstrncpy
- 989 Pickling QColor fails
- 987 Disconnecting a signal that has not been connected
- 973 shouldInterruptJavaScript slot override is never called
- 966 QX11Info.display() missing
- 959 can't pass QVariant to the QtWebkit bridge
- 1006 Segfault in QLabel init
- 1002 Segmentation fault on PySide/Spyder exit
- 998 Segfault with Spyder after switching to another app
- 995 QDeclarativeView.itemAt returns faulty reference. (leading to SEGFAULT)
- 990 Segfault when trying to disconnect a signal that is not connected
- 975 Possible memory leak
- 991 The __repr__ of various types is broken
- 988 The type supplied with currentChanged signal in QTabWidget has changed in 1.0.6

1.0.6 (2011-08-22)
------------------

Major changes
~~~~~~~~~~~~~

- New documentation layout;
- Fixed some regressions from the last release (1.0.5);
- Optimizations during anonymous connection;

Bug fixes
~~~~~~~~~

- 972 anchorlayout.py of graphicsview example raised a unwriteable memory exception when exits
- 953 Segfault when QObject is garbage collected after QTimer.singeShot
- 951 ComponentComplete not called on QDeclarativeItem subclass
- 965 Segfault in QtUiTools.QUiLoader.load
- 958 Segmentation fault with resource files
- 944 Segfault on QIcon(None).pixmap()
- 941 Signals with QtCore.Qt types as arguments has invalid signatures
- 964 QAbstractItemView.moveCursor() method is missing
- 963 What's This not displaying QTableWidget column header information as in Qt Designer
- 961 QColor.__repr__/__str__ should be more pythonic
- 960 QColor.__reduce__ is incorrect for HSL colors
- 950 implement Q_INVOKABLE
- 940 setAttributeArray/setUniformValueArray do not take arrays
- 931 isinstance() fails with Signal instances
- 928 100's of QGraphicItems with signal connections causes slowdown
- 930 Documentation mixes signals and functions.
- 923 Make QScriptValue (or QScriptValueIterator) implement the Python iterator protocol
- 922 QScriptValue's repr() should give some information about its data
- 900 QtCore.Property as decorator
- 895 jQuery version is outdated, distribution code de-duplication breaks documentation search
- 731 Can't specify more than a single 'since' argument
- 983 copy.deepcopy raises SystemError with QColor
- 947 NETWORK_ERR during interaction QtWebKit window with server
- 873 Deprecated methods could emit DeprecationWarning
- 831 PySide docs would have a "Inherited by" list for each class

1.0.5 (2011-07-22)
------------------

Major changes
~~~~~~~~~~~~~

- Widgets present on "ui" files are exported in the root widget, check PySide ML thread for more information[1];
- pyside-uic generate menubars without parent on MacOS plataform;
- Signal connection optimizations;

Bug fixes
~~~~~~~~~

- 892 Segfault when destructing QWidget and QApplication has event filter installed
- 407 Crash while multiple inheriting with QObject and native python class
- 939 Shiboken::importModule must verify if PyImport_ImportModule succeeds
- 937 missing pid method in QProcess
- 927 Segfault on QThread code.
- 925 Segfault when passing a QScriptValue as QObject or when using .toVariant() on a QScriptValue
- 905 QtGui.QHBoxLayout.setMargin function call is created by pyside-uic, but this is not available in the pyside bindings
- 904 Repeatedly opening a QDialog with Qt.WA_DeleteOnClose set crashes PySide
- 899 Segfault with 'QVariantList' Property.
- 893 Shiboken leak reference in the parent control
- 878 Shiboken may generate incompatible modules if a new class is added.
- 938 QTemporaryFile JPEG problem
- 934 A __getitem__ of QByteArray behaves strange
- 929 pkg-config files do not know about Python version tags
- 926 qmlRegisterType does not work with QObject
- 924 Allow QScriptValue to be accessed via []
- 921 Signals not automatically disconnected on object destruction
- 920 Cannot use same slot for two signals
- 919 Default arguments on QStyle methods not working
- 915 QDeclarativeView.scene().addItem(x) make the x object invalid
- 913 Widgets inside QTabWidget are not exported as members of the containing widget
- 910 installEventFilter() increments reference count on target object
- 907 pyside-uic adds MainWindow.setMenuBar(self.menubar) to the generated code under OS X
- 903 eventFilter in ItemDelegate
- 897 QObject.property() and QObject.setProperty() methods fails for user-defined properties
- 896 QObject.staticMetaObject() is missing
- 916 Missing info about when is possible to use keyword arguments in docs [was: QListWidgetItem's constructor ignores text parameter]
- 890 Add signal connection example for valueChanged(int) on QSpinBox to the docs
- 821 Mapping interface for QPixmapCache
- 909 Deletion of QMainWindow/QApplication leads to segmentation fault
