# Script generated with Bloom
pkgdesc="ROS - The libg2o library from http://openslam.org/g2o.html"
url='https://github.com/RainerKuemmerle/g2o'

pkgname='ros-lunar-libg2o'
pkgver='2017.4.2_2'
pkgrel=1
arch=('any')
license=('BSD'
)

makedepends=('boost'
'cmake'
'eigen3'
'mesa'
'suitesparse'
)

depends=('boost'
'eigen3'
'mesa'
'ros-lunar-catkin'
'suitesparse'
)

conflicts=()
replaces=()

_dir=libg2o
source=()
md5sums=()

prepare() {
    cp -R $startdir/libg2o $srcdir/libg2o
}

build() {
  # Use ROS environment variables
  source /usr/share/ros-build-tools/clear-ros-env.sh
  [ -f /opt/ros/lunar/setup.bash ] && source /opt/ros/lunar/setup.bash

  # Create build directory
  [ -d ${srcdir}/build ] || mkdir ${srcdir}/build
  cd ${srcdir}/build

  # Fix Python2/Python3 conflicts
  /usr/share/ros-build-tools/fix-python-scripts.sh -v 2 ${srcdir}/${_dir}

  # Build project
  cmake ${srcdir}/${_dir} \
        -DCMAKE_BUILD_TYPE=Release \
        -DCATKIN_BUILD_BINARY_PACKAGE=ON \
        -DCMAKE_INSTALL_PREFIX=/opt/ros/lunar \
        -DPYTHON_EXECUTABLE=/usr/bin/python2 \
        -DPYTHON_INCLUDE_DIR=/usr/include/python2.7 \
        -DPYTHON_LIBRARY=/usr/lib/libpython2.7.so \
        -DPYTHON_BASENAME=-python2.7 \
        -DSETUPTOOLS_DEB_LAYOUT=OFF
  make
}

package() {
  cd "${srcdir}/build"
  make DESTDIR="${pkgdir}/" install
}

