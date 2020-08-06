---
title: 사용자 지정 어셈블리에서 사용 권한 어설션 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- secure calls [Reporting Services]
- custom assemblies [Reporting Services], permissions
- permission sets [Reporting Services]
- asserting permissions
- permissions [Reporting Services], custom assemblies
- limited permission sets
- security configuration files [Reporting Services]
ms.assetid: 3afb9631-f15e-405e-990b-ee102828f298
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: cba3c0b74712b6b4d0f6b5c58925cfd562f0df77
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87638550"
---
# <a name="asserting-permissions-in-custom-assemblies"></a><span data-ttu-id="9235c-102">사용자 지정 어셈블리에서 권한 어설션</span><span class="sxs-lookup"><span data-stu-id="9235c-102">Asserting Permissions in Custom Assemblies</span></span>
  <span data-ttu-id="9235c-103">기본적으로 사용자 지정 어셈블리 코드는 제한된 **Execution** 권한 집합으로 실행됩니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-103">By default, custom assembly code runs with the limited **Execution** permission set.</span></span> <span data-ttu-id="9235c-104">경우에 따라 보안 시스템 내에서 보호된 리소스(파일, 레지스트리 등)에 대한 보안 호출을 하는 사용자 지정 어셈블리를 구현하고자 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-104">In some cases, you may wish to implement a custom assembly that makes secured calls to protected resources within your security system (such as a file or the registry).</span></span> <span data-ttu-id="9235c-105">이렇게 하려면 다음 작업을 수행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-105">In order to accomplish this, you must do the following:</span></span>  
  
1.  <span data-ttu-id="9235c-106">코드에서 보안 호출을 하는 데 필요한 정확한 권한을 식별합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-106">Identify the exact permissions that your code needs in order to make the secured call.</span></span> <span data-ttu-id="9235c-107">이 메서드가 라이브러리의 일부인 경우 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] 이 정보는 메서드 설명서에 포함 되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-107">If this method is part of a [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] library, this information should be included in the method documentation.</span></span>  
  
2.  <span data-ttu-id="9235c-108">사용자 지정 어셈블리에 필요한 권한을 부여하기 위해 보고서 서버 정책 구성 파일을 수정합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-108">Modify the report server policy configuration files in order to grant the custom assembly the required permissions.</span></span> <span data-ttu-id="9235c-109">보안 정책 구성 파일에 대한 자세한 내용은 [Reporting Services 보안 정책 파일 사용](../extensions/secure-development/using-reporting-services-security-policy-files.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9235c-109">For more information about the security policy configuration files, see [Using Reporting Services Security Policy Files](../extensions/secure-development/using-reporting-services-security-policy-files.md).</span></span>  
  
3.  <span data-ttu-id="9235c-110">필요한 권한을 보안 호출이 이루어지는 메서드의 일부로 어설션합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-110">Assert the required permissions as part of the method in which the secure call is made.</span></span> <span data-ttu-id="9235c-111">보고서 서버에서 호출되는 사용자 지정 어셈블리 코드는 보고서 식 호스트 어셈블리의 일부로서 기본적으로 **Execution** 권한을 사용하여 실행되므로 이 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-111">This is required because the custom assembly code that is called by the report server is part of the report expression host assembly, which runs with **Execution** permission by default.</span></span> <span data-ttu-id="9235c-112">**Execution** 권한 집합을 통해 코드를 실행할 수 있지만 보호된 리소스는 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-112">The **Execution** permission set enables code to run, but not to use protected resources.</span></span>  
  
4.  <span data-ttu-id="9235c-113">강력한 이름으로 서명된 경우 사용자 지정 어셈블리를 **AllowPartiallyTrustedCallersAttribute**로 표시합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-113">Mark the custom assembly with **AllowPartiallyTrustedCallersAttribute** if it is signed with a strong name.</span></span> <span data-ttu-id="9235c-114">사용자 지정 어셈블리는 기본적으로 **FullTrust**가 부여되지 않는(즉, "부분적으로 신뢰할 수 있는" 호출자) 보고서 식 호스트 어셈블리의 일부인 보고서 식에서 호출되므로 이 작업이 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-114">This is required because custom assemblies are called from a report expression that is part of the report expression host assembly, which, by default, is not granted **FullTrust**; thus it is a "partially trusted" caller.</span></span> <span data-ttu-id="9235c-115">자세한 내용은 [강력한 이름의 사용자 지정 어셈블리 사용](using-strong-named-custom-assemblies.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9235c-115">For more information, see [Using Strong-Named Custom Assemblies](using-strong-named-custom-assemblies.md).</span></span>  
  
## <a name="implementing-a-secure-call"></a><span data-ttu-id="9235c-116">보안 호출 구현</span><span class="sxs-lookup"><span data-stu-id="9235c-116">Implementing a Secure Call</span></span>  
 <span data-ttu-id="9235c-117">정책 구성 파일을 수정하여 어셈블리별 권한을 부여할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-117">You can modify the policy configuration files to grant your assembly specific permissions.</span></span> <span data-ttu-id="9235c-118">예를 들어, 통화 변환을 처리하도록 사용자 지정 어셈블리를 작성하는 경우 파일에서 현재 통화 환율을 읽어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-118">For example, if you were writing a custom assembly to handle currency conversion, you might need to read the current currency exchange rates from a file.</span></span> <span data-ttu-id="9235c-119">환율 정보를 검색하려면 어셈블리에 대한 권한 집합에 추가 보안 권한 **FileIOPermission**을 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-119">To retrieve the rate information, you would need to add an additional security permission, **FileIOPermission**, to your permission set for the assembly.</span></span> <span data-ttu-id="9235c-120">정책 구성 파일에서 다음 추가 항목을 입력할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-120">You can make the following additional entry in the policy configuration file:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="CurrencyRatesFilePermissionSet"  
   Description="A special permission set that grants read access to my currency rates file.">  
      <IPermission class="FileIOPermission"  
         version="1"  
         Read="C:\CurrencyRates.xml"/>  
      <IPermission class="SecurityPermission"  
         version="1"  
         Flags="Execution, Assertion"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="9235c-121">그런 다음 해당 권한 집합을 참조하는 코드 그룹을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-121">You then add a code group that references that permission set:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="CurrencyRatesFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\MSSQL\Reporting Services\ReportServer\bin\CurrencyConversion.dll"/>  
</CodeGroup>  
```  
  
 <span data-ttu-id="9235c-122">코드에 올바른 권한이 부여되려면 사용자 지정 어셈블리 코드 내에서 권한을 어설션해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-122">In order for your code to acquire the appropriate permission, you must assert the permission within your custom assembly code.</span></span> <span data-ttu-id="9235c-123">예를 들어, XML 파일 C:\CurrencyRates.xml에 읽기 전용 액세스 권한을 추가하려면 다음 코드를 메서드에 추가해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-123">For example, if you want to add read-only access to an XML file, C:\CurrencyRates.xml, you must add the following code to your method:</span></span>  
  
```  
// C#  
FileIOPermission permission = new FileIOPermission(FileIOPermissionAccess.Read, @"C:\CurrencyRates.xml");  
try  
{  
   permission.Assert();  
   // Load the XML currency rates file  
   XmlDocument doc = new XmlDocument();  
   doc.Load(@"C:\CurrencyRates.xml");  
...  
```  
  
 <span data-ttu-id="9235c-124">또한 어설션을 메서드 특성 형태로 추가할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9235c-124">You can also add the assertion as a method attribute:</span></span>  
  
```  
[FileIOPermissionAttribute(SecurityAction.Assert, Read=@"C:\CurrencyRates.xml")]  
```  
  
 <span data-ttu-id="9235c-125">자세한 내용은 .NET Framework 개발자 가이드의 ".NET Framework Security(.NET Framework 보안)"를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9235c-125">For more information, see ".NET Framework Security" in the .NET Framework Developer's Guide.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9235c-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9235c-126">See Also</span></span>  
 [<span data-ttu-id="9235c-127">보고서에서 사용자 지정 어셈블리 사용</span><span class="sxs-lookup"><span data-stu-id="9235c-127">Using Custom Assemblies with Reports</span></span>](using-custom-assemblies-with-reports.md)  
  
  
