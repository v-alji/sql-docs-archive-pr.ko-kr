---
title: 대상 서버의 암호화 옵션 설정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent, encryption
- target servers [SQL Server], encryption
- multiserver environments [SQL Server], setting encryption options on target servers
ms.assetid: 1a9fd539-e166-4ea8-9f21-ac400ca74dee
author: stevestein
ms.author: sstein
ms.openlocfilehash: cd10d2e05e59015542f41cc123de993e6128f9f6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87659786"
---
# <a name="set-encryption-options-on-target-servers"></a><span data-ttu-id="3cfd6-102">대상 서버의 암호화 옵션 설정</span><span class="sxs-lookup"><span data-stu-id="3cfd6-102">Set Encryption Options on Target Servers</span></span>
  <span data-ttu-id="3cfd6-103">마스터 서버와 대상 서버 중 일부 또는 모두 간의 SSL(Secure Sockets Layer) 암호화 통신을 위해 인증서를 사용할 수는 없지만 마스터 서버와 대상 서버 간의 채널을 암호화하려는 경우 대상 서버에서 필요한 보안 수준을 사용하도록 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-103">If you cannot use a certificate for Secure Sockets Layer (SSL) encrypted communications between master servers and some or all of your target servers, but you want to encrypt the channel between them, configure the target server to use the level of security required.</span></span>  
  
 <span data-ttu-id="3cfd6-104">특정 마스터 서버/대상 서버 통신 채널에 필요한 적절 한 보안 수준을 구성 하려면 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 대상 서버의 에이전트 레지스트리 하위 키 **\ HKEY_LOCAL_MACHINE \software\microsoft\microsoft \\ SQL Server** \<*instance_name*> **\SQLServerAgent\MsxEncryptChannelOptions (REG_DWORD)** 를 다음 값 중 하나로 설정 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-104">To configure the appropriate level of security required for a specific master server/target server communication channel, set the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent registry subkey **\HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Microsoft SQL Server\\**\<*instance_name*>**\SQLServerAgent\MsxEncryptChannelOptions(REG_DWORD)** on the target server to one of the following values.</span></span> <span data-ttu-id="3cfd6-105">의 값은 \<*instance_name*> **MSSQL입니다.** _n_.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-105">The value of \<*instance_name*> is **MSSQL.**_n_.</span></span> <span data-ttu-id="3cfd6-106">예를 들어 **MSSQL.1** 또는 **MSSQL.3**입니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-106">For example, **MSSQL.1** or **MSSQL.3**.</span></span>  
  
|<span data-ttu-id="3cfd6-107">값</span><span class="sxs-lookup"><span data-stu-id="3cfd6-107">Value</span></span>|<span data-ttu-id="3cfd6-108">Description</span><span class="sxs-lookup"><span data-stu-id="3cfd6-108">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="3cfd6-109">**0**</span><span class="sxs-lookup"><span data-stu-id="3cfd6-109">**0**</span></span>|<span data-ttu-id="3cfd6-110">이 대상 서버와 마스터 서버 간에 암호화를 사용하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-110">Disables encryption between this target server and the master server.</span></span> <span data-ttu-id="3cfd6-111">대상 서버와 마스터 서버 간의 채널이 다른 방법으로 보호되는 경우에만 이 옵션을 선택합니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-111">Choose this option only when the channel between the target server and master server is secured by another means.</span></span>|  
|<span data-ttu-id="3cfd6-112">**1**</span><span class="sxs-lookup"><span data-stu-id="3cfd6-112">**1**</span></span>|<span data-ttu-id="3cfd6-113">이 대상 서버와 마스터 서버 간에만 암호화를 사용하지만 인증서 확인은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-113">Enables encryption only between this target server and the master server, but no certificate validation is required.</span></span>|  
|<span data-ttu-id="3cfd6-114">**2**</span><span class="sxs-lookup"><span data-stu-id="3cfd6-114">**2**</span></span>|<span data-ttu-id="3cfd6-115">이 대상 서버와 마스터 서버 간에 전체 SSL 암호화와 인증서 확인을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-115">Enables full SSL encryption and certificate validation between this target server and the master server.</span></span> <span data-ttu-id="3cfd6-116">이 설정은 기본값입니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-116">This setting is the default.</span></span> <span data-ttu-id="3cfd6-117">다른 값을 선택할 구체적인 이유가 없으면 이 설정을 변경하지 않는 것이 좋습니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-117">Unless you have specific reason to choose a different value, we recommend not changing it.</span></span>|  
  
 <span data-ttu-id="3cfd6-118">**1** 또는 **2** 를 지정하는 경우 마스터 서버와 대상 서버에서 모두 SSL을 사용해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-118">If **1** or **2** is specified, you must have SSL enabled on both the master and target servers.</span></span> <span data-ttu-id="3cfd6-119">**2** 를 지정하는 경우 마스터 서버에 제대로 서명된 인증서도 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="3cfd6-119">If **2** is specified, you must also have a properly signed certificate present on the master server.</span></span>  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoteRegistry](../../includes/ssnoteregistry-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3cfd6-120">참고 항목</span><span class="sxs-lookup"><span data-stu-id="3cfd6-120">See Also</span></span>  
 [<span data-ttu-id="3cfd6-121">데이터베이스 엔진에 암호화 연결 사용&#40;SQL Server 구성 관리자&#41;</span><span class="sxs-lookup"><span data-stu-id="3cfd6-121">Enable Encrypted Connections to the Database Engine &#40;SQL Server Configuration Manager&#41;</span></span>](../../database-engine/configure-windows/enable-encrypted-connections-to-the-database-engine.md)  
  
  
