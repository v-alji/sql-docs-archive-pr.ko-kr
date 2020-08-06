---
title: 구성 관리용 WMI 공급자 작업 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: wmi
ms.topic: reference
helpviewer_keywords:
- permissions [WMI]
- connection strings [WMI]
- security [WMI]
- WMI Provider for Configuration Management, connection strings
- WMI Provider for Configuration Management, security
- late binding [WMI]
- WMI Provider for Configuration Management, late binding
- binding [WMI]
ms.assetid: 34daa922-7074-41d0-9077-042bb18c222a
author: CarlRabeler
ms.author: carlrab
ms.openlocfilehash: 80f311fb0abae2337f6ea4a5d5d85aaa0d320b94
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87650836"
---
# <a name="working-with-the-wmi-provider-for-configuration-management"></a><span data-ttu-id="08af4-102">구성 관리용 WMI 공급자 작업</span><span class="sxs-lookup"><span data-stu-id="08af4-102">Working with the WMI Provider for Configuration Management</span></span>
  <span data-ttu-id="08af4-103">컴퓨터 관리용 WMI 공급자를 사용하여 프로그래밍하기 전에 다음을 고려합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-103">Consider the following before programming with the WMI Provider for Computer Management:</span></span>  
  
## <a name="binding"></a><span data-ttu-id="08af4-104">바인딩</span><span class="sxs-lookup"><span data-stu-id="08af4-104">Binding</span></span>  
 <span data-ttu-id="08af4-105">구성 관리용 WMI 공급자는 COM 개체 모델이며 초기 바인딩과 런타임에 바인딩을 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-105">The WMI Provider for Configuration Management is a COM object model and it supports early and late binding.</span></span> <span data-ttu-id="08af4-106">런타임에 바인딩의 경우 VBScript와 같은 스크립트 언어를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스, 네트워크 설정 및 별칭을 프로그래밍 방식으로 조작할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-106">With late binding you can use script languages, such as VBScript, to manipulate the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services, network settings, and aliases programmatically.</span></span>  
  
 <span data-ttu-id="08af4-107">스크립트 언어를 사용 하 여 WMI 공급자 구현을 프로그래밍 하는 방법에 대 한 자세한 내용은 [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [웹 사이트](https://go.microsoft.com/fwlink/?linkid=15426)를 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="08af4-107">For further information about programming WMI Provider implementations using scripting languages, see the [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="specifying-a-connection-string"></a><span data-ttu-id="08af4-108">연결 문자열 지정</span><span class="sxs-lookup"><span data-stu-id="08af4-108">Specifying a Connection String</span></span>  
 <span data-ttu-id="08af4-109">애플리케이션은 공급자가 정의한 WMI 네임스페이스에 연결하여 구성 관리용 WMI 공급자를 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스로 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-109">Applications direct the WMI Provider for Configuration Management to an instance of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] by connecting to a WMI namespace defined by the provider.</span></span> <span data-ttu-id="08af4-110">Windows WMI 서비스는 이 네임스페이스를 공급자 DLL에 매핑하여 메모리에 로드합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-110">The Windows WMI service maps this namespace to the provider DLL and loads it into memory.</span></span> <span data-ttu-id="08af4-111">모든 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 인스턴스는 단일 WMI 네임스페이스로 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-111">All instances of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] are represented with a single WMI namespace.</span></span> <span data-ttu-id="08af4-112">기본 네임스페이스는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-112">The namespace defaults to</span></span>  
  
```  
\\.\root\Microsoft\SqlServer\ComputerManagement12\instance_name  
```  
  
 <span data-ttu-id="08af4-113">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 기본 설치에서 `instance_name`의 기본값은 `MSSQLSERVER`입니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-113">where `instance_name` defaults to `MSSQLSERVER` in a default installation of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="08af4-114">**참고:** Windows 방화벽을 통해 연결 하는 경우에는 컴퓨터가 적절히 구성 되어 있는지 확인 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-114">**Note:** If you are connecting through Windows Firewall you will need to make sure your computers are configured appropriately.</span></span> <span data-ttu-id="08af4-115">[!INCLUDE[msCoName](../../includes/msconame-md.md)]MSDN [웹 사이트](https://go.microsoft.com/fwlink/?linkid=15426)의 WMI(Windows Management Instrumentation) 설명서에서 "Windows 방화벽을 통해 연결" 문서를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08af4-115">See the "Connecting Through Windows Firewall" article in the Windows Management Instrumentation documentation on [!INCLUDE[msCoName](../../includes/msconame-md.md)] MSDN [Web site](https://go.microsoft.com/fwlink/?linkid=15426).</span></span>  
  
## <a name="permissions-and-server-authentication"></a><span data-ttu-id="08af4-116">권한과 서버 인증</span><span class="sxs-lookup"><span data-stu-id="08af4-116">Permissions and Server Authentication</span></span>  
 <span data-ttu-id="08af4-117">구성 관리용 WMI 공급자에 액세스하려면 클라이언트 WMI 관리 스크립트가 대상 컴퓨터에서 관리자 컨텍스트로 실행되고 있어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-117">To access the WMI Provider for Configuration Management, the client WMI management script must be running in the context of an administrator on the target computer.</span></span> <span data-ttu-id="08af4-118">관리할 컴퓨터에서 로컬 Windows Administrators 그룹의 멤버여야 합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-118">You need to be a member of the local Windows administrators group on the computer you want to manage.</span></span>  
  
 <span data-ttu-id="08af4-119">관리자는 그룹 정책을 설정하여 WMI 공급자에 대한 사용자 액세스를 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-119">The administrator can set group policies to control user access to WMI providers.</span></span> <span data-ttu-id="08af4-120">그룹 정책 설정에 대한 자세한 내용은 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 구성 관리자 도움말의 "그룹 정책 및 MMC"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="08af4-120">For more information about setting group policies see "Group Policy and MMC" in the [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Configuration Manager Help.</span></span>  
  
 <span data-ttu-id="08af4-121">WMI 관리 스크립트를 사용하여 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 서비스가 실행되는 계정을 업데이트할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-121">The WMI management script can be used to update the account under which [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] services run.</span></span>  
  
 <span data-ttu-id="08af4-122">구성 관리용 WMI 공급자는 보안 인증서를 지원합니다.</span><span class="sxs-lookup"><span data-stu-id="08af4-122">Security certificates are supported by the WMI Provider for Configuration Management.</span></span> <span data-ttu-id="08af4-123">인증서에 대 한 자세한 내용은 [암호화 계층](../security/encryption/encryption-hierarchy.md)을 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="08af4-123">For more information about certificates, see [Encryption Hierarchy](../security/encryption/encryption-hierarchy.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08af4-124">참고 항목</span><span class="sxs-lookup"><span data-stu-id="08af4-124">See Also</span></span>  
 [<span data-ttu-id="08af4-125">SQL Server 구성 관리자</span><span class="sxs-lookup"><span data-stu-id="08af4-125">SQL Server Configuration Manager</span></span>](../sql-server-configuration-manager.md)  
  
  
