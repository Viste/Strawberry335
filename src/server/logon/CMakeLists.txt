# Copyright (C) 2005-2011 MaNGOS <http://www.getmangos.com/>
#
# Copyright (C) 2008-2011 Trinity <http://www.trinitycore.org/>
#
# Copyright (C) 2010-2011 Project SkyFire <http://www.projectskyfire.org/>
#
# This file is free software; as a special exception the author gives
# unlimited permission to copy and/or distribute it, with or without
# modifications, as long as this notice is preserved.
#
# This program is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY, to the extent permitted by law; without even the
# implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

if( USE_COREPCH )
  include_directories(${CMAKE_CURRENT_BINARY_DIR})
endif()

file(GLOB_RECURSE sources_Accounts Accounts/*.cpp Accounts/*.h)
file(GLOB_RECURSE sources_Achievements Achievements/*.cpp Achievements/*.h)
file(GLOB_RECURSE sources_Addons Addons/*.cpp Addons/*.h)
file(GLOB_RECURSE sources_AutoBroadcast AutoBroadcast/*.cpp AutoBroadcast/*.h)
file(GLOB_RECURSE sources_Battleground Battleground/*.cpp Battleground/*.h)
file(GLOB_RECURSE sources_Cache Cache/*.cpp Cache/*.h)
file(GLOB_RECURSE sources_Chat Chat/*.cpp Chat/*.h)
file(GLOB_RECURSE sources_Chat_Commands Chat/Commands/*.cpp Chat/Commands/*.h)
file(GLOB_RECURSE sources_Character Character/*.cpp Character/*.h)
file(GLOB_RECURSE sources_Database Database/*.cpp Database/*.h)
file(GLOB_RECURSE sources_DataStores DataStores/*.cpp DataStores/*.h)
file(GLOB_RECURSE sources_Groups Groups/*.cpp Groups/*.h)
file(GLOB_RECURSE sources_Handler Handler/*.cpp Handler/*.h)
file(GLOB_RECURSE sources_Logon Logon/*.cpp Logon/*.h)
file(GLOB_RECURSE sources_Maps Maps/*.cpp Maps/*.h)
file(GLOB_RECURSE sources_Misc Misc/*.cpp Misc/*.h)
file(GLOB_RECURSE sources_Objects Objects/*.cpp Objects/*.h)
file(GLOB_RECURSE sources_Server Server/*.cpp Server/*.h)
file(GLOB_RECURSE sources_Server_Client Server/Client/*.cpp Server/Client/*.h)
file(GLOB_RECURSE sources_Server_Control Server/Control/*.cpp Server/Control/*.h)
file(GLOB_RECURSE sources_Server_Node Server/Node/*.cpp Server/Node/*.h)
file(GLOB_RECURSE sources_Server_Protocol Server/Protocol/*.cpp Server/Protocol/*.h)
file(GLOB_RECURSE sources_Server_Generics Server/Generics/*.cpp Server/Generics/*.h)
file(GLOB_RECURSE sources_Tickets Tickets/*.cpp Tickets/*.h)
file(GLOB_RECURSE sources_Warden Warden/*.cpp Warden/*.h)

source_group(CMake FILES CMakeLists.txt)
source_group(Accounts FILES ${sources_Accounts})
source_group(Achievements FILES ${sources_Achievements})
source_group(Addons FILES ${sources_Addons})
source_group(AutoBroadcast FILES ${sources_AutoBroadcast})
source_group(Battleground FILES ${sources_Battleground})
source_group(Cache FILES ${sources_Cache})
source_group(Chat\\Commands FILES ${sources_Chat_Commands})
source_group(Chat\\Chat FILES ${sources_Chat})
source_group(Character FILES ${sources_Character})
source_group(Database FILES ${sources_Database})
source_group(DataStores FILES ${sources_DataStores})
source_group(Groups FILES ${sources_Groups})
source_group(Handler FILES ${sources_Handler})
source_group(Logon FILES ${sources_Logon})
source_group(Maps FILES ${sources_Maps})
source_group(Misc FILES ${sources_Misc})
source_group(Objects FILES ${sources_Objects})
source_group(Server\\Client FILES ${sources_Server_Client})
source_group(Server\\Control FILES ${sources_Server_Control})
source_group(Server\\Node FILES ${sources_Server_Node})
source_group(Server\\Protocol FILES ${sources_Server_Protocol})
source_group(Server\\Generics FILES ${sources_Server_Generics})
source_group(Server\\Server FILES ${sources_Server})
source_group(Tickets FILES ${sources_Tickets})
source_group(Warden FILES ${sources_Warden})

# Create logon-libary

if( USE_COREPCH AND MSVC )
  set(logon_STAT_SRCS
    PrecompiledHeaders/logonPCH.cpp
    PrecompiledHeaders/logonPCH.h
  )
endif()

set(logon_STAT_SRCS
  ${logon_STAT_SRCS}
  ${sources_Accounts}
  ${sources_Achievements}
  ${sources_Addons}
  ${sources_AutoBroadcast}
  ${sources_Battleground}
  ${sources_Cache}
  ${sources_Chat}
  ${sources_Chat_Commands}
  ${sources_Character}
  ${sources_Database}
  ${sources_DataStores}
  ${sources_Handler}
  ${sources_Logon}
  ${sources_Maps}
  ${sources_Misc}
  ${sources_Objects}
  ${sources_Server}
  ${sources_Tickets}
  ${sources_Warden}
)

include_directories(
  ${CMAKE_BINARY_DIR}
  ${CMAKE_SOURCE_DIR}/dep/mersennetwister
  ${CMAKE_SOURCE_DIR}/dep/SFMT
  ${CMAKE_SOURCE_DIR}/dep/zlib
  ${CMAKE_SOURCE_DIR}/src/server/collision
  ${CMAKE_SOURCE_DIR}/src/server/collision/Management
  ${CMAKE_SOURCE_DIR}/src/server/shared
  ${CMAKE_SOURCE_DIR}/src/server/shared/Configuration
  ${CMAKE_SOURCE_DIR}/src/server/shared/Cryptography
  ${CMAKE_SOURCE_DIR}/src/server/shared/Cryptography/Authentication
  ${CMAKE_SOURCE_DIR}/src/server/shared/Database
  ${CMAKE_SOURCE_DIR}/src/server/shared/DataStores
  ${CMAKE_SOURCE_DIR}/src/server/shared/Debugging
  ${CMAKE_SOURCE_DIR}/src/server/shared/Dynamic/CountedReference
  ${CMAKE_SOURCE_DIR}/src/server/shared/Dynamic/LinkedReference
  ${CMAKE_SOURCE_DIR}/src/server/shared/Dynamic
  ${CMAKE_SOURCE_DIR}/src/server/shared/Logging
  ${CMAKE_SOURCE_DIR}/src/server/shared/Networking
  ${CMAKE_SOURCE_DIR}/src/server/shared/Networking/Headers
  ${CMAKE_SOURCE_DIR}/src/server/shared/Networking/Sockets
  ${CMAKE_SOURCE_DIR}/src/server/shared/Networking/Strategies
  ${CMAKE_SOURCE_DIR}/src/server/shared/Packets
  ${CMAKE_SOURCE_DIR}/src/server/shared/Policies
  ${CMAKE_SOURCE_DIR}/src/server/shared/Threading
  ${CMAKE_SOURCE_DIR}/src/server/shared/Utilities
  ${CMAKE_CURRENT_SOURCE_DIR}
  ${CMAKE_CURRENT_SOURCE_DIR}/Accounts
  ${CMAKE_CURRENT_SOURCE_DIR}/Achievements
  ${CMAKE_CURRENT_SOURCE_DIR}/Addons
  ${CMAKE_CURRENT_SOURCE_DIR}/AutoBroadcast
  ${CMAKE_CURRENT_SOURCE_DIR}/Battleground
  ${CMAKE_CURRENT_SOURCE_DIR}/Cache
  ${CMAKE_CURRENT_SOURCE_DIR}/Chat
  ${CMAKE_CURRENT_SOURCE_DIR}/Chat/Commands
  ${CMAKE_CURRENT_SOURCE_DIR}/Character
  ${CMAKE_CURRENT_SOURCE_DIR}/Database
  ${CMAKE_CURRENT_SOURCE_DIR}/DataStores
  ${CMAKE_CURRENT_SOURCE_DIR}/Groups
  ${CMAKE_CURRENT_SOURCE_DIR}/Handler
  ${CMAKE_CURRENT_SOURCE_DIR}/Logon
  ${CMAKE_CURRENT_SOURCE_DIR}/Maps
  ${CMAKE_CURRENT_SOURCE_DIR}/Misc
  ${CMAKE_CURRENT_SOURCE_DIR}/Objects
  ${CMAKE_CURRENT_SOURCE_DIR}/PrecompiledHeader
  ${CMAKE_CURRENT_SOURCE_DIR}/Server
  ${CMAKE_CURRENT_SOURCE_DIR}/Server/Generics
  ${CMAKE_CURRENT_SOURCE_DIR}/Server/Protocol
  ${CMAKE_CURRENT_SOURCE_DIR}/Server/Client
  ${CMAKE_CURRENT_SOURCE_DIR}/Server/Node
  ${CMAKE_CURRENT_SOURCE_DIR}/Server/Control
  ${CMAKE_CURRENT_SOURCE_DIR}/Tickets
  ${CMAKE_CURRENT_SOURCE_DIR}/Warden
  ${CMAKE_SOURCE_DIR}/src/server/scripts/PrecompiledHeaders
  ${ACE_INCLUDE_DIR}
  ${MYSQL_INCLUDE_DIR}
  ${OPENSSL_INCLUDE_DIR}
)

add_library(logon OBJECT ${logon_STAT_SRCS})

# Generate precompiled header
if( USE_COREPCH )
  if(CMAKE_COMPILER_IS_GNUCXX)
    add_precompiled_header(logon ${CMAKE_CURRENT_SOURCE_DIR}/PrecompiledHeaders/logonPCH.h)
  elseif(MSVC)
    add_native_precompiled_header(logon ${CMAKE_CURRENT_SOURCE_DIR}/PrecompiledHeaders/logonPCH)
  endif()
endif()
