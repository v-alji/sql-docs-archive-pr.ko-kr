---
title: Reporting Services의 권한 부여 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- authorization [Reporting Services]
ms.assetid: 15fc1c7b-560c-4737-b126-e0d428a1b530
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7420b45175ca0b0a5fc66da4a7939b07b79c75b7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651513"
---
# <a name="authorization-in-reporting-services"></a><span data-ttu-id="ec035-102">Reporting Services의 권한 부여</span><span class="sxs-lookup"><span data-stu-id="ec035-102">Authorization in Reporting Services</span></span>
  <span data-ttu-id="ec035-103">권한 부여는 보고서 서버 데이터베이스의 지정된 리소스에 대해 요청된 유형의 액세스 권한을 ID에 부여해야 하는지 여부를 결정하는 과정입니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-103">Authorization is the process of determining whether an identity should be granted the requested type of access to a given resource in the report server database.</span></span> [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]<span data-ttu-id="ec035-104">는 애플리케이션에 대한 사용자의 역할 할당을 기준으로 지정된 리소스에 대한 액세스 권한을 사용자에게 부여하는 역할 기반 권한 부여 아키텍처입니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-104">uses a role-based authorization architecture that grants a user access to a given resource based on the user's role assignment for the application.</span></span> <span data-ttu-id="ec035-105">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 에 대한 보안 확장 프로그램에는 사용자가 보고서 서버에서 인증되면 사용자에게 액세스 권한을 부여하는 데 사용되는 권한 부여 구성 요소의 구현이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-105">Security extensions for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] contain an implementation of an authorization component that is used to grant access to users once they are authenticated on the report server.</span></span> <span data-ttu-id="ec035-106">권한 부여는 사용자가 SOAP API 및 URL 액세스를 통해 시스템 또는 보고서 서버 항목에 대한 작업을 수행하려고 시도할 때 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-106">Authorization is invoked when a user attempts to perform an operation on the system or a report server item through the SOAP API and via URL access.</span></span> <span data-ttu-id="ec035-107">보안 확장 프로그램 인터페이스 **IAuthorizationExtension**을 통해 이 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-107">This is made possible through the security extension interface **IAuthorizationExtension**.</span></span> <span data-ttu-id="ec035-108">앞에서 언급한 대로 모든 확장 프로그램은 배포되는 모든 확장 프로그램에 대한 **IExtension** 기본 인터페이스에서 상속됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-108">As stated previously, all extensions inherit from **IExtension** the base interface for any extension that you deploy.</span></span> <span data-ttu-id="ec035-109">**IExtension** 및 **IAuthorizationExtension** 은 **Microsoft.ReportingServices.Interfaces** 네임스페이스의 멤버입니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-109">**IExtension** and **IAuthorizationExtension** are members of the **Microsoft.ReportingServices.Interfaces** namespace.</span></span>

## <a name="checking-access"></a><span data-ttu-id="ec035-110">액세스 권한 확인</span><span class="sxs-lookup"><span data-stu-id="ec035-110">Checking Access</span></span>
 <span data-ttu-id="ec035-111">권한 부여에서 사용자 지정 보안 구현의 핵심은 액세스 권한 확인으로, 이 동작은 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 메서드에 구현됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-111">In authorization, the key to any custom security implementation is the access check, which is implemented in the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span> <span data-ttu-id="ec035-112"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>는 사용자가 보고서 서버에서 작업을 시도할 때마다 호출됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-112"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> is called each time a user attempts an operation on the report server.</span></span> <span data-ttu-id="ec035-113"><xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 메서드는 각 작업 유형에 대해 오버로드됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-113">The <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method is overloaded for each operation type.</span></span> <span data-ttu-id="ec035-114">폴더 작업의 경우 액세스 권한 확인의 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-114">For folder operations, an example of an access check might look like the following:</span></span>

```
// Overload for Folder operations
public bool CheckAccess(
   string userName, 
   IntPtr userToken, 
   byte[] secDesc, 
   FolderOperation requiredOperation)
{
   // If the user is the administrator, allow unrestricted access.
   if (userName == m_adminUserName) 
      return true;

   AceCollection acl = DeserializeAcl(secDesc);
   foreach(AceStruct ace in acl)
   {
         if (userName == ace.PrincipalName)
         {
            foreach(FolderOperation aclOperation in 
               ace.FolderOperations)
            {
               if (aclOperation == requiredOperation)
                     return true;
            }
         }
   }
   return false;
}
```

 <span data-ttu-id="ec035-115">보고서 서버는 로그온한 사용자의 이름, 사용자 토큰, 항목에 대한 보안 설명자 및 요청된 작업을 전달하여 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-115">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method by passing in the name of the logged-on user, a user token, the security descriptor for the item, and the requested operation.</span></span> <span data-ttu-id="ec035-116">여기서 보안 설명자를 검토하여 요청을 완료할 사용자 이름과 해당하는 적절한 권한이 있는지 확인합니다. 그런 다음 액세스 권한이 부여되었음을 나타내는 `true`가 반환되거나 액세스 권한이 거부되었음을 나타내는 `false`가 반환됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-116">Here you would check the security descriptor for the user name and the appropriate permission to complete the request, then return `true` to signify that access is granted or `false` to signify access is denied.</span></span>

## <a name="security-descriptors"></a><span data-ttu-id="ec035-117">보안 설명자</span><span class="sxs-lookup"><span data-stu-id="ec035-117">Security Descriptors</span></span>
 <span data-ttu-id="ec035-118">보고서 서버 데이터베이스의 항목에 대해 권한 부여 정책을 설정할 때 보고서 관리자와 같은 클라이언트 애플리케이션에서는 항목에 대한 보안 정책과 함께 사용자 정보를 보안 확장 프로그램에 제출합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-118">When setting authorization policies on items in the report server database, a client application (such as Report Manager) submits the user information to the security extension along with a security policy for the item.</span></span> <span data-ttu-id="ec035-119">이 보안 정책과 사용자 정보를 통칭하여 보안 설명자라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-119">This security policy and user information are known collectively as a security descriptor.</span></span> <span data-ttu-id="ec035-120">보안 설명자에는 보고서 서버 데이터베이스의 항목에 대한 다음 정보가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-120">A security descriptor contains the following information for an item in the report server database:</span></span>

-   <span data-ttu-id="ec035-121">항목에 대한 작업을 수행할 수 있는 특정 유형의 권한을 가진 그룹 또는 사용자</span><span class="sxs-lookup"><span data-stu-id="ec035-121">The group or user that has some type of permission to perform operations on the item.</span></span>

-   <span data-ttu-id="ec035-122">항목의 형식</span><span class="sxs-lookup"><span data-stu-id="ec035-122">The item's type.</span></span>

-   <span data-ttu-id="ec035-123">항목에 대한 액세스를 제어하는 DACL(임의 액세스 제어 목록)</span><span class="sxs-lookup"><span data-stu-id="ec035-123">A discretionary access control list controlling access to the item.</span></span>

 <span data-ttu-id="ec035-124">보안 설명자는 웹 서비스의 <xref:ReportService2010.ReportingService2010.SetPolicies%2A> 및 <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> 메서드를 사용하여 만들어집니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-124">Security descriptors are created using the Web service <xref:ReportService2010.ReportingService2010.SetPolicies%2A> and <xref:ReportService2010.ReportingService2010.SetSystemPolicies%2A> methods.</span></span>

### <a name="authorization-flow"></a><span data-ttu-id="ec035-125">권한 부여 흐름</span><span class="sxs-lookup"><span data-stu-id="ec035-125">Authorization Flow</span></span>
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="ec035-126">권한 부여는 현재 서버에서 실행되도록 구성된 보안 확장 프로그램에서 제어됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-126">authorization is controlled by the security extension currently configured to run on the server.</span></span> <span data-ttu-id="ec035-127">권한 부여는 역할 기반으로 이루어지며 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 보안 아키텍처에서 제공되는 권한과 작업으로 제한됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-127">Authorization is role-based and limited to the permissions and operations supplied by the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] security architecture.</span></span> <span data-ttu-id="ec035-128">다음 다이어그램은 사용자가 보고서 서버 데이터베이스의 항목에 대해 작업을 수행할 수 있도록 권한을 부여하는 과정을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-128">The following diagram depicts the process of authorizing users to operate on items in the report server database:</span></span>

 <span data-ttu-id="ec035-129">![Reporting Services 보안 권한 부여 흐름](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services 보안 권한 부여 흐름")</span><span class="sxs-lookup"><span data-stu-id="ec035-129">![Reporting Services security authorization flow](../../media/rosettasecurityextensionauthorizationflow.gif "Reporting Services security authorization flow")</span></span>

 <span data-ttu-id="ec035-130">이 다이어그램에 나타난 대로 권한 부여는 다음 순서를 따릅니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-130">As shown in this diagram, authorization follows this sequence:</span></span>

1.  <span data-ttu-id="ec035-131">인증되면 클라이언트 애플리케이션에서 Reporting Services 웹 서비스 메서드를 통해 보고서 서버에 요청합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-131">Once authenticated, client applications make requests to the report server through the Reporting Services Web service methods.</span></span> <span data-ttu-id="ec035-132">인증 티켓이 각 웹 요청의 HTTP 헤더에서 쿠키의 형태로 보고서 서버에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-132">An authentication ticket is passed to the report server in the form of a cookie in the HTTP header of each Web request.</span></span>

2.  <span data-ttu-id="ec035-133">쿠키는 액세스 권한 확인 전에 검사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-133">The cookie is validated prior to any access check.</span></span>

3.  <span data-ttu-id="ec035-134">쿠키가 검사되면 보고서 서버에서 <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A>를 호출하고 사용자에게 ID가 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-134">Once the cookie is validated, the report server calls <xref:Microsoft.ReportingServices.Interfaces.IAuthenticationExtension.GetUserInfo%2A> and the user is given an identity.</span></span>

4.  <span data-ttu-id="ec035-135">사용자가 Reporting Services 웹 서비스를 통해 작업을 시도합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-135">The user attempts an operation through the Reporting Services Web service.</span></span>

5.  <span data-ttu-id="ec035-136">보고서 서버에서 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> 메서드를 호출합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-136">The report server calls the <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A> method.</span></span>

6.  <span data-ttu-id="ec035-137">보안 설명자가 검색되고 <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>의 사용자 지정 보안 확장 구현에 전달됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-137">The security descriptor is retrieved and passed to a custom security extension implementation of <xref:Microsoft.ReportingServices.Interfaces.IAuthorizationExtension.CheckAccess%2A>.</span></span> <span data-ttu-id="ec035-138">이 시점에서 사용자, 그룹 또는 컴퓨터는 액세스할 항목의 보안 설명자와의 대조를 통한 확인을 거치고 요청된 작업을 수행할 수 있도록 권한이 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-138">At this point, the user, group, or computer is compared to the security descriptor of the item being accessed and is authorized to perform the requested operation.</span></span>

7.  <span data-ttu-id="ec035-139">사용자에게 권한이 부여되면 웹 서비스에서 작업을 수행하고 응답을 호출 애플리케이션에 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="ec035-139">If the user is authorized, the Web service performs the operation and returns a response to the calling application.</span></span>


