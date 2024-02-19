# BILLETERA BITCOIN

Bienvenido a _Billetera bitcoin_¡Una aplicación de pago de Bitcoin independiente para su dispositivo Android!

Este proyecto contiene varios subcproyectos:

 * __Cartera__:
 La aplicación Android en sí. Esto es probablemente lo que estás buscando. 
 * __Mercado__:
     App description and promo material for the Google Play app store.


### REQUISITOS PREVIOS PARA LA CONSTRUCCIÓN

You'll need git, a Java 11 SDK and Gradle between 4.4 and 6.9.x for this. We'll assume Ubuntu 22.04 LTS (Jammy Jellyfish)
for the package installs, which comes with OpenJDK 11 and Gradle 4.4.1 out of the box.

    # primera vez sólo
    sudo apt install git gradle openjdk-11-jdk

Create a directory for the Android SDK (e.g. `android-sdk`) and point the `ANDROID_HOME` variable to it.

Download the [Android SDK Tools](https://developer.android.com/studio/index.html#command-tools)
and unpack it to `$ANDROID_HOME/`.

Finally, the last preparative step is acquiring the source code. Again in your workspace, use:

    # first time only
    git clone -b main https://github.com/bitcoin-wallet/bitcoin-wallet.git bitcoin-wallet
    cd bitcoin-wallet


### BUILDING

You can build all sub-projects in all flavors at once using Gradle:

    # each time
    gradle clean build

For details about building the wallet see the [specific README](wallet/README.md).


### REPRODUCIBLE BUILD

Alternatively, you can build using buildah:

    # each time
    buildah build --cap-add sys_admin --device /dev/fuse --file build.Containerfile --output build/ .

Access to FUSE and the SYS_ADMIN capability are needed for mounting disorderfs
in order to sort the directory entries of the project folder.

The unsigned APKs are written to the specified output directory.
