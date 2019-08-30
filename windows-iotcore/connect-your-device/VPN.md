---
title: VPN en Windows 10 IoT Core
author: saraclay
ms.author: saclayt
ms.date: 11/19/2018
ms.topic: article
description: Aprenda a usar, configurar y configurar las funcionalidades de VPN para el dispositivo de Windows 10 IoT Core.
keywords: Windows IOT, VPN, instalación, dispositivo
ms.openlocfilehash: 94eafcb74a05179a7741cb516b5e7be30b525092
ms.sourcegitcommit: 2b4ce105834c294dcdd8f332ac8dd2732f4b5af8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "60167903"
---
# <a name="leveraging-vpn-capabilities-for-your-windows-10-iot-core-device"></a><span data-ttu-id="be1e9-104">Aprovechamiento de las funcionalidades de VPN para el dispositivo de Windows 10 IoT Core</span><span class="sxs-lookup"><span data-stu-id="be1e9-104">Leveraging VPN capabilities for your Windows 10 IoT Core device</span></span>

<span data-ttu-id="be1e9-105">Para aprovechar las funcionalidades de VPN de Windows 10 IoT Core, siga las instrucciones que se indican a continuación.</span><span class="sxs-lookup"><span data-stu-id="be1e9-105">In order to leverage the VPN capabilities of Windows 10 IoT Core, follow the instructions below.</span></span>

> [!NOTE]
> <span data-ttu-id="be1e9-106">La mayoría de las instrucciones siguientes deben adaptarse.</span><span class="sxs-lookup"><span data-stu-id="be1e9-106">Most of the instructions below must be adapted.</span></span> <span data-ttu-id="be1e9-107">Son específicos del host de VPN al que se está conectando el usuario.</span><span class="sxs-lookup"><span data-stu-id="be1e9-107">They are specific to the VPN host that the user is connecting to.</span></span> <span data-ttu-id="be1e9-108">Los certificados utilizados son ejemplos.</span><span class="sxs-lookup"><span data-stu-id="be1e9-108">The certs used are examples.</span></span>

## <a name="establishing-a-vpn-connection"></a><span data-ttu-id="be1e9-109">Establecer una conexión VPN</span><span class="sxs-lookup"><span data-stu-id="be1e9-109">Establishing a VPN connection</span></span> 

1. <span data-ttu-id="be1e9-110">Obtenga los certificados necesarios y cópielo en el dispositivo de IoT (por ejemplo, en una carpeta \vpntest).</span><span class="sxs-lookup"><span data-stu-id="be1e9-110">Obtain the necessary certs and copy to your IoT device (e.g. to a \vpntest folder).</span></span>

* <span data-ttu-id="be1e9-111">RASTest. pfx</span><span class="sxs-lookup"><span data-stu-id="be1e9-111">RASTest.pfx</span></span>
* <span data-ttu-id="be1e9-112">IssuingCA. CRL</span><span class="sxs-lookup"><span data-stu-id="be1e9-112">IssuingCA.crl</span></span>
* <span data-ttu-id="be1e9-113">RootCA. CRL</span><span class="sxs-lookup"><span data-stu-id="be1e9-113">RootCA.crl</span></span>

2. <span data-ttu-id="be1e9-114">Aplique los certificados de la máquina local a.</span><span class="sxs-lookup"><span data-stu-id="be1e9-114">Apply local machine certs a.</span></span> <span data-ttu-id="be1e9-115">PowerShell en el dispositivo como administrador</span><span class="sxs-lookup"><span data-stu-id="be1e9-115">PowerShell into device as administrator</span></span>

```powershell
certmgr -add .\IssuingCA.crl -r localmachine -s root
certmgr -add .\RootCA.crl -r localmachine -s root
```

3. <span data-ttu-id="be1e9-116">Aplique los certificados de usuario a.</span><span class="sxs-lookup"><span data-stu-id="be1e9-116">Apply user certs a.</span></span> <span data-ttu-id="be1e9-117">Inicie sesión en el dispositivo IoT con SSH como "DefaultAccount".</span><span class="sxs-lookup"><span data-stu-id="be1e9-117">Login to the IoT Device using SSH as "DefaultAccount".</span></span>
<span data-ttu-id="be1e9-118">b.</span><span class="sxs-lookup"><span data-stu-id="be1e9-118">b.</span></span> <span data-ttu-id="be1e9-119">En el símbolo del sistema, escriba "PowerShell".</span><span class="sxs-lookup"><span data-stu-id="be1e9-119">From the command prompt, type "PowerShell".</span></span>
<span data-ttu-id="be1e9-120">c.</span><span class="sxs-lookup"><span data-stu-id="be1e9-120">c.</span></span> <span data-ttu-id="be1e9-121">Emita los siguientes comandos desde PowerShell (mientras está conectado como "cuenta predeterminada"):</span><span class="sxs-lookup"><span data-stu-id="be1e9-121">Issue the following commands from PowerShell (while logged in as "Default Account"):</span></span>

```powershell
$mypwd = ConvertTo-SecureString -String "<password>" -Force -AsPlainText
import-pfxcertificate -FilePath RasTest.pfx -CertStoreLocation cert:currentUser\my -Password $mypwd

Cert -add .\IssuingCA.crl -r currentuser -s my
certmgr -add .\RootCA.crl -r currentuser -s my
```

4. <span data-ttu-id="be1e9-122">Corregir el archivo de hosts agregar una entrada en el archivo c:\windows\system32\driverS\etc\hosts (ejemplo que se muestra a continuación);</span><span class="sxs-lookup"><span data-stu-id="be1e9-122">Fix hosts file Add an entry into c:\windows\system32\driverS\etc\hosts file (example shown below);</span></span>

> |    |    |    |
> |----|----| ---|
> | <span data-ttu-id="be1e9-123">10.10.10.10</span><span class="sxs-lookup"><span data-stu-id="be1e9-123">10.10.10.10</span></span> | <span data-ttu-id="be1e9-124">MyVPN.DomainName.org</span><span class="sxs-lookup"><span data-stu-id="be1e9-124">MyVPN.DomainName.org</span></span> | <span data-ttu-id="be1e9-125">Reemplazar por la dirección IP y el nombre de dominio según sea necesario</span><span class="sxs-lookup"><span data-stu-id="be1e9-125">Replace with IP address and domain name as needed</span></span> |

5. <span data-ttu-id="be1e9-126">Cree la aplicación de prueba de VPN y reemplace "MyVPN.DomainName.org" en el código fuente.</span><span class="sxs-lookup"><span data-stu-id="be1e9-126">Build the VPN test app Replace the "MyVPN.DomainName.org" in the source code.</span></span> <span data-ttu-id="be1e9-127">Aumente el aumento según sea necesario.</span><span class="sxs-lookup"><span data-stu-id="be1e9-127">Augment further as needed.</span></span>

6. <span data-ttu-id="be1e9-128">Implemente el código siguiente en la sección "Inicio y detención de una conexión VPN" en el dispositivo IoT de Windows 10.</span><span class="sxs-lookup"><span data-stu-id="be1e9-128">Deploy the code below in the "Starting and stopping a VPN Connection" section to the Windows 10 IoT device.</span></span>
<span data-ttu-id="be1e9-129">Escriba un "nombre de perfil" arbitrario y haga clic en el botón "conectar con VPN".</span><span class="sxs-lookup"><span data-stu-id="be1e9-129">Enter an arbitrary "Profile name" and press the "Connect to VPN" button.</span></span> 


## <a name="starting-and-stopping-a-vpn-connection"></a><span data-ttu-id="be1e9-130">Inicio y detención de una conexión VPN</span><span class="sxs-lookup"><span data-stu-id="be1e9-130">Starting and stopping a VPN connection</span></span>

<span data-ttu-id="be1e9-131">Use el código siguiente para iniciar y detener una conexión VPN.</span><span class="sxs-lookup"><span data-stu-id="be1e9-131">Use the code below to start and stop a VPN connection.</span></span>

```csharp

  private async Task ConnectVPNProfile()
        {
            string vpnProfileName = "MyVPNProfileName";

            string[] epdg = { "MyVPN.DomainName.org" };
            VpnManagementErrorStatus status = VpnManagementErrorStatus.Ok;
            IAsyncOperation<VpnManagementErrorStatus> op;

            var vpnMa = new VpnManagementAgent();
            var vpnProfile = new VpnNativeProfile();
            vpnProfile.AlwaysOn = true;
            vpnProfile.ProfileName = vpnProfileName;
            vpnProfile.RequireVpnClientAppUI = true;
            vpnProfile.RememberCredentials = true;
            vpnProfile.RoutingPolicyType = VpnRoutingPolicyType.SplitRouting;
            vpnProfile.TunnelAuthenticationMethod = VpnAuthenticationMethod.Eap;
            vpnProfile.UserAuthenticationMethod = VpnAuthenticationMethod.Eap;
            foreach (var s in epdg)
            {
                vpnProfile.Servers.Add(s);
            }

            vpnProfile.EapConfiguration = GetEapXmlString();

            // Adds the profile using the management api.
           status = await vpnMa.AddProfileFromObjectAsync(vpnProfile);
            Debug.WriteLine($"Add profile: {status}");
            TextBlockLog.Text += $"Add profile: {status}\r\n";

            await Task.Delay(1000);

            op = vpnMa.ConnectProfileAsync(vpnProfile);
            status = await op;
            Debug.WriteLine($"Connect succeeded: {status}");
            TextBlockLog.Text += $"Connect profile: {status}\r\n";


        }


  public static string GetEapXmlString()
        {
            //string template = "<EapHostConfig xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">25</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>25</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV1\"><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><FastReconnect>true</FastReconnect><InnerEapOptional>false</InnerEapOptional><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>true</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>d2 d3 8e ba 60 ca a1 c1 20 55 a2 e1 c8 3b 15 ad 45 01 10 c2 </TrustedRootCA><TrustedRootCA>d1 76 97 cc 20 6e d2 6e 1a 51 f5 bb 96 e9 35 6d 6d 61 0b 74 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><EKUMapping><EKUMap><EKUName>AAD Conditional Access</EKUName><EKUOID>1.3.6.1.4.1.311.87</EKUOID></EKUMap></EKUMapping><ClientAuthEKUList Enabled=\"true\"><EKUMapInList><EKUName>AAD Conditional Access</EKUName></EKUMapInList></ClientAuthEKUList></FilteringInfo></TLSExtensions></EapType></Eap><EnableQuarantineChecks>false</EnableQuarantineChecks><RequireCryptoBinding>true</RequireCryptoBinding><PeapExtensions><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">true</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/MsPeapConnectionPropertiesV2\">false</AcceptServerName></PeapExtensions></EapType></Eap></Config></EapHostConfig>";
            string template = "<EapHostConfig xmlns =\"http://www.microsoft.com/provisioning/EapHostConfig\"><EapMethod><Type xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">13</Type><VendorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorId><VendorType xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</VendorType><AuthorId xmlns=\"http://www.microsoft.com/provisioning/EapCommon\">0</AuthorId></EapMethod><Config xmlns=\"http://www.microsoft.com/provisioning/EapHostConfig\"><Eap xmlns=\"http://www.microsoft.com/provisioning/BaseEapConnectionPropertiesV1\"><Type>13</Type><EapType xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV1\"><CredentialsSource><CertificateStore><SimpleCertSelection>true</SimpleCertSelection></CertificateStore></CredentialsSource><ServerValidation><DisableUserPromptForServerValidation>false</DisableUserPromptForServerValidation><ServerNames></ServerNames><TrustedRootCA>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </TrustedRootCA></ServerValidation><DifferentUsername>false</DifferentUsername><PerformServerValidation xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</PerformServerValidation><AcceptServerName xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\">false</AcceptServerName><TLSExtensions xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV2\"><FilteringInfo xmlns=\"http://www.microsoft.com/provisioning/EapTlsConnectionPropertiesV3\"><CAHashList Enabled=\"true\"><IssuerHash>b6 ea bf ba 48 be 09 c9 50 4f c6 ea 9b f5 74 dc a9 01 56 62 </IssuerHash></CAHashList></FilteringInfo></TLSExtensions></EapType></Eap></Config></EapHostConfig>";
            //TODO: Create propper XML here
            string result = template;

            return result;
        }
```







