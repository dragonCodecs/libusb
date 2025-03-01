# SPDX-License-Identifier: BSD-3-Clause
# SPDX-FileCopyrightText: 2023 L. E. Segovia <amy@amyspark.me>

examples = [
	'dpfp',
	'hotplugtest',
	'listdevs',
	'sam3u_benchmark',
	'testlibusb',
	'xusb',
]

foreach example: examples
	executable(
		example,
		files(
			'@0@.c'.format(example)
		),
		c_args: c_args,
		dependencies: libusb_dep,
		install: false,
		native: native,
	)
endforeach

executable(
	'dpfp_threaded',
	files(
		'dpfp.c'
	),
	cpp_args: c_args + ['-DDPFP_THREADED'],
	dependencies: [libusb_dep, thread_dep],
	install: false,
	native: native,
)

ezusb_lib = static_library(
	'ezusb',
	files(
		'ezusb.c'
	),
	c_args: c_args,
	dependencies: libusb_dep,
	install: false,
	native: native,
)

executable(
	'fxload',
	files(
		'fxload.c',
	),
	c_args: c_args + ['-DDPFP_THREADED'],
	dependencies: libusb_dep,
	link_with: ezusb_lib,
	install: false,
	native: native,
)
