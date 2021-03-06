macro(SIGAR_TEST name)
	add_executable(${name} ${name}.c)
	target_link_libraries(${name}  sigar)
	add_test(${name} ${name})
endmacro(SIGAR_TEST name)

include_directories(../include/)

if(CMAKE_SYSTEM_NAME STREQUAL "Linux")
  add_definitions(-DSIGAR_TEST_OS_LINUX)
endif(CMAKE_SYSTEM_NAME STREQUAL "Linux")

if(CMAKE_SYSTEM_NAME MATCHES "(Darwin|FreeBSD)")
  add_definitions(-DSIGAR_TEST_OS_DARWIN)
endif(CMAKE_SYSTEM_NAME MATCHES "(Darwin|FreeBSD)")

if(CMAKE_SYSTEM_NAME MATCHES "(Solaris|SunOS)" )
  add_definitions(-DSIGAR_TEST_OS_SOLARIS)
endif(CMAKE_SYSTEM_NAME MATCHES "(Solaris|SunOS)" )

if(CMAKE_SYSTEM_NAME MATCHES "(hpux)" )
  add_definitions(-DSIGAR_TEST_OS_HPUX)
endif(CMAKE_SYSTEM_NAME MATCHES "(hpux)" )

if(CMAKE_SYSTEM_NAME MATCHES "(AIX)" )
  add_definitions(-DSIGAR_TEST_OS_AIX)
endif(CMAKE_SYSTEM_NAME MATCHES "(AIX)" )

if(WIN32)
  add_definitions(-DSIGAR_TEST_OS_WIN32)
endif(WIN32)

SIGAR_TEST(t_sigar_cpu)
SIGAR_TEST(t_sigar_fs)
SIGAR_TEST(t_sigar_loadavg)
SIGAR_TEST(t_sigar_mem)
SIGAR_TEST(t_sigar_netconn)
SIGAR_TEST(t_sigar_netif)
SIGAR_TEST(t_sigar_pid)
SIGAR_TEST(t_sigar_proc)
SIGAR_TEST(t_sigar_reslimit)
SIGAR_TEST(t_sigar_swap)
SIGAR_TEST(t_sigar_sysinfo)
SIGAR_TEST(t_sigar_uptime)
SIGAR_TEST(t_sigar_version)
