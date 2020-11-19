set(
    FLAC_SRCS
    flac/src/libFLAC/bitmath.c
    flac/src/libFLAC/bitreader.c
    flac/src/libFLAC/bitwriter.c
    flac/src/libFLAC/cpu.c
    flac/src/libFLAC/crc.c
    flac/src/libFLAC/fixed.c
    flac/src/libFLAC/fixed_intrin_sse2.c
    flac/src/libFLAC/fixed_intrin_ssse3.c
    flac/src/libFLAC/float.c
    flac/src/libFLAC/format.c
    flac/src/libFLAC/lpc.c
    flac/src/libFLAC/lpc_intrin_avx2.c
    flac/src/libFLAC/lpc_intrin_sse2.c
    flac/src/libFLAC/lpc_intrin_sse41.c
    flac/src/libFLAC/lpc_intrin_sse.c
    flac/src/libFLAC/md5.c
    flac/src/libFLAC/memory.c
    flac/src/libFLAC/metadata_iterators.c
    flac/src/libFLAC/metadata_object.c
    flac/src/libFLAC/stream_decoder.c
    flac/src/libFLAC/stream_encoder.c
    flac/src/libFLAC/stream_encoder_framing.c
    flac/src/libFLAC/stream_encoder_intrin_avx2.c
    flac/src/libFLAC/stream_encoder_intrin_sse2.c
    flac/src/libFLAC/stream_encoder_intrin_ssse3.c
    flac/src/libFLAC/window.c
)

set(
	FLAC_PRIV
	flac/src/libFLAC/include
	flac/include
	)
configure_file ("${CMAKE_CURRENT_LIST_DIR}/flac/config.cmake.h.in"
                "${CMAKE_CURRENT_LIST_DIR}/flac/src/libFLAC/include/config.h")

idf_component_register(SRCS ${FLAC_SRCS}
                       INCLUDE_DIRS ${FLAC_PRIV}
                   	  )
target_compile_definitions(${COMPONENT_LIB} PRIVATE HAVE_CONFIG_H)
target_compile_definitions(${COMPONENT_LIB} PRIVATE SIZE_T_MAX=0xffffffff)
