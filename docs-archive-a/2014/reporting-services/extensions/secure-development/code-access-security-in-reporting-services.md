---
title: Reporting Services의 코드 액세스 보안 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- code groups [Reporting Services]
- code access security [Reporting Services]
- permission sets [Reporting Services]
- evidence [Reporting Services]
- code access security [Reporting Services], about code access security
- named permission sets [Reporting Services]
ms.assetid: 97480368-1fc3-4c32-b1b0-63edfb54e472
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: ebe023b13a003895845bbb119f0bc93a0d01203a
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661535"
---
# <a name="code-access-security-in-reporting-services"></a><span data-ttu-id="973ae-102">Reporting Services의 코드 액세스 보안</span><span class="sxs-lookup"><span data-stu-id="973ae-102">Code Access Security in Reporting Services</span></span>
  <span data-ttu-id="973ae-103">코드 액세스 보안은 증명 정보, 코드 그룹 및 명명된 권한 집합 등의 핵심 개념을 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-103">Code access security centers on these core concepts: evidence, code groups, and named permission sets.</span></span> <span data-ttu-id="973ae-104">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 보고서 관리자, 보고서 디자이너 및 보고서 서버 구성 요소에는 각각 데이터, 배달, 렌더링 및 보안 확장 프로그램뿐만 아니라 사용자 지정 어셈블리에 대한 코드 액세스 보안을 구성하는 정책 파일이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-104">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], the Report Manager, Report Designer, and Report Server components each have a policy file that configures code access security for custom assemblies as well as data, delivery, rendering, and security extensions.</span></span> <span data-ttu-id="973ae-105">다음 섹션에서는 코드 액세스 보안에 대한 개요를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-105">The following sections provide an overview of code access security.</span></span> <span data-ttu-id="973ae-106">이 섹션에서 다루는 항목에 대한 자세한 내용은 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK 설명서의 “보안 정책 모델”을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="973ae-106">For more detailed information about the topics covered in this section, see "Security Policy Model" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="973ae-107">보고서 서버가 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 기술을 기반으로 빌드되어도 일반적인 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 애플리케이션과 보고서 서버는 상당히 다르기 때문에 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)]는 코드 액세스 보안을 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-107">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses code access security because, although the report server is built on [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] technology, there is a substantial difference between a typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application and the report server.</span></span> <span data-ttu-id="973ae-108">일반적인 [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] 애플리케이션은 사용자 코드를 실행하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-108">A typical [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)] application does not execute user code.</span></span> <span data-ttu-id="973ae-109">반면 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]는 사용자가 보고서 정의 언어의 **Code** 요소를 사용하여 보고서 정의 파일에 대해 프로그래밍 작업을 수행하고 보고서에 사용할 특수화된 기능을 사용자 지정 어셈블리로 개발해 넣을 수 있도록 하는 확장 가능한 개방형 아키텍처를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-109">In contrast, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] uses an open and extensible architecture that allows users to program against the report definition files using the **Code** element of the Report Definition Language and to develop specialized functionality into a custom assembly for use in reports.</span></span> <span data-ttu-id="973ae-110">또한 개발자는 보고서 서버의 기능을 향상시키는 강력한 확장 프로그램을 설계하고 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-110">Furthermore, developers can design and deploy powerful extensions that enhance the capabilities of the report server.</span></span> <span data-ttu-id="973ae-111">이러한 기능과 유연성으로 인해 가능한 한 강력한 보호 및 보안을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-111">With this power and flexibility comes the need to provide as much protection and security as possible.</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] <span data-ttu-id="973ae-112">개발자는 자신의 보고서에 임의의 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 어셈블리를 사용하고 전역 어셈블리 캐시에 배포된 어셈블리의 모든 기능을 기본적으로 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-112">developers can use any [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] assembly in their reports and natively call upon all of the functionality of assemblies deployed to the global assembly cache.</span></span> <span data-ttu-id="973ae-113">보고서 서버에서는 보고서 식 및 로드된 사용자 지정 어셈블리에 대해 부여할 사용 권한만 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-113">The only thing that the report server can control is what permissions are given for report expressions and loaded custom assemblies.</span></span> <span data-ttu-id="973ae-114">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 사용자 지정 어셈블리에는 기본적으로 **실행** 전용 권한만 부여됩니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-114">In [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)], custom assemblies receive **Execute**-only permissions by default.</span></span>  
  
## <a name="evidence"></a><span data-ttu-id="973ae-115">증명 정보</span><span class="sxs-lookup"><span data-stu-id="973ae-115">Evidence</span></span>  
 <span data-ttu-id="973ae-116">증명 정보는 CLR(공용 언어 런타임)이 코드 어셈블리에 대한 보안 정책을 확인하기 위해 사용하는 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-116">Evidence is the information that the common language runtime (CLR) uses to determine a security policy for code assemblies.</span></span> <span data-ttu-id="973ae-117">증명 정보는 코드에 특정한 특징이 있음을 런타임에 알립니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-117">Evidence indicates to the runtime that code has a particular characteristic.</span></span> <span data-ttu-id="973ae-118">증명 정보의 일반적인 형식에는 디지털 서명 및 어셈블리의 위치가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-118">Common forms of evidence include digital signatures and the location of an assembly.</span></span> <span data-ttu-id="973ae-119">애플리케이션에 의미가 있는 다른 정보를 나타내도록 증명 정보를 사용자 지정 설계할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-119">Evidence can also be custom designed to represent other information that is meaningful to the application.</span></span>  
  
 <span data-ttu-id="973ae-120">어셈블리 및 애플리케이션 도메인은 모두 증명 정보를 기반으로 사용 권한을 받습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-120">Both assemblies and application domains receive permissions based on evidence.</span></span> <span data-ttu-id="973ae-121">예를 들어 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]가 액세스를 시도하는 어셈블리의 위치는 짧은 이름이 지정된 어셈블리의 일반적인 증명 정보 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-121">For example, the location of an assembly that [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is attempting to access is one common form of evidence for weak-named assemblies.</span></span> <span data-ttu-id="973ae-122">이를 URL 증명 정보라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-122">This is known as URL evidence.</span></span> <span data-ttu-id="973ae-123">보고서 서버에 배포된 사용자 지정 데이터 처리 확장 프로그램에 대한 URL 증명 정보는 "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-123">URL evidence for a custom data processing extension deployed to a report server might be "C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll".</span></span> <span data-ttu-id="973ae-124">어셈블리의 강력한 이름 또는 디지털 서명은 증명 정보의 다른 일반적인 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-124">The strong name or digital signature of an assembly is another common form of evidence.</span></span> <span data-ttu-id="973ae-125">이 경우 증명 정보는 어셈블리에 대한 공개 키 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-125">In this case, the evidence is the public key information for an assembly.</span></span>  
  
## <a name="code-groups"></a><span data-ttu-id="973ae-126">코드 그룹</span><span class="sxs-lookup"><span data-stu-id="973ae-126">Code Groups</span></span>  
 <span data-ttu-id="973ae-127">코드 그룹은 멤버 자격에 대한 조건이 지정되어 있는 논리적 코드 그룹입니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-127">A code group is a logical grouping of code that has a specified condition for membership.</span></span> <span data-ttu-id="973ae-128">멤버 자격 조건을 충족하는 모든 코드는 이 그룹에 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-128">Any code that meets the membership condition is included in the group.</span></span> <span data-ttu-id="973ae-129">관리자는 코드 그룹 및 연결된 권한 집합을 관리하여 보안 정책을 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-129">Administrators configure a security policy by managing code groups and their associated permission sets.</span></span>  
  
 <span data-ttu-id="973ae-130">코드 그룹에 대한 멤버 자격 조건은 증명 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-130">A membership condition for a code group is based on evidence.</span></span> <span data-ttu-id="973ae-131">예를 들어 코드 그룹에 대한 URL 멤버 자격은 URL 증명 정보를 기반으로 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-131">For example, a URL membership for a code group is based on URL evidence.</span></span> <span data-ttu-id="973ae-132">CLR(공용 언어 런타임)은 URL 증명 정보와 같은 식별 특징을 사용하여 코드를 설명하고 그룹의 멤버 자격 조건이 충족되는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-132">The common language runtime (CLR) uses identifying characteristics such as URL evidence to describe the code and to determine whether a group's membership condition has been met.</span></span> <span data-ttu-id="973ae-133">예를 들어 코드 그룹의 멤버 자격 조건이 "어셈블리 C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll의 코드"인 경우 런타임은 증명 정보를 통해 코드가 해당 위치에서 발생되는지 여부를 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-133">For example, if the membership condition of a code group is "code in the assembly C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll", the runtime examines the evidence to determine whether the code originates from that location.</span></span> <span data-ttu-id="973ae-134">이 유형의 코드 그룹에 대한 구성 항목 예는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-134">An example of a configuration entry for this type of code group might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="FullTrust"  
   Name="MyCodeGroup"  
   Description="Code group for my data processing extension">  
      <IMembershipCondition class="UrlMembershipCondition"  
         version="1"  
         Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\Microsoft.Samples.ReportingServices.FsiDataExtension.dll"  
       />  
</CodeGroup>  
```  
  
 <span data-ttu-id="973ae-135">시스템 관리자 또는 애플리케이션 배포 전문가와 협력하여 사용자 지정 어셈블리 또는 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 확장 프로그램에 필요한 유형의 코드 액세스 보안 및 코드 그룹을 확인해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-135">You should work with your system administrator or application deployment expert to determine the type of code access security and code groups that your custom assemblies or [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions require.</span></span>  
  
## <a name="named-permission-sets"></a><span data-ttu-id="973ae-136">명명된 권한 집합</span><span class="sxs-lookup"><span data-stu-id="973ae-136">Named Permission Sets</span></span>  
 <span data-ttu-id="973ae-137">명명된 권한 집합은 관리자가 코드 그룹에 연결할 수 있는 권한 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-137">A named permission set is a set of permissions that administrators can associate with a code group.</span></span> <span data-ttu-id="973ae-138">대부분의 명명된 권한 집합은 하나 이상의 권한, 이름 및 해당 권한 집합에 대한 설명으로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-138">Most named permission sets consist of at least one permission, a name, and description for the permission set.</span></span> <span data-ttu-id="973ae-139">관리자는 명명된 권한 집합을 사용하여 코드 그룹에 대한 보안 정책을 설정하거나 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-139">Administrators can use named permission sets to establish or modify the security policy for code groups.</span></span> <span data-ttu-id="973ae-140">둘 이상의 코드 그룹을 이름이 같은 명명된 권한 집합에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-140">More than one code group can be associated with the same named permission set.</span></span> <span data-ttu-id="973ae-141">CLR은 **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything** 및 **FullTrust** 등의 명명된 기본 제공 권한 집합을 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-141">The CLR provides built-in named permission sets; among these are **Nothing**, **Execution**, **Internet**, **LocalIntranet**, **Everything**, and **FullTrust**.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="973ae-142">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 사용자 지정 데이터, 배달, 렌더링 및 보안 확장 프로그램은 **FullTrust** 권한 집합으로 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-142">Custom data, delivery, rendering, and security extensions in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] must run under the **FullTrust** permission set.</span></span> <span data-ttu-id="973ae-143">시스템 관리자와 협력하여 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 확장 프로그램에 적합한 코드 그룹 및 멤버 자격 조건을 추가하십시오.</span><span class="sxs-lookup"><span data-stu-id="973ae-143">Work with your system administrator to add the appropriate code group and membership conditions for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] extensions.</span></span>  
  
 <span data-ttu-id="973ae-144">사용하는 사용자 지정 어셈블리에 대한 고유한 사용자 지정 권한 수준을 보고서에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-144">You can associate your own custom levels of permissions for custom assemblies that you use with reports.</span></span> <span data-ttu-id="973ae-145">예를 들어 어셈블리가 특정 파일에 액세스할 수 있도록 하려면 특정 파일 I/O 액세스 권한으로 명명된 권한 집합을 새로 만든 다음 코드 그룹에 이 권한 집합을 할당할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-145">For example, if you want to allow an assembly to access a specific file, you can create a new named permission set with specific file I/O access and then assign the permission set to your code group.</span></span> <span data-ttu-id="973ae-146">다음 권한 집합은 파일 MyFile.xml에 읽기 전용 액세스 권한을 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-146">The following permission set grants read-only access to the file MyFile.xml:</span></span>  
  
```  
<PermissionSet class="NamedPermissionSet"  
   version="1"  
   Name="MyNewFilePermissionSet"  
   Description="A special permission set that grants read access to my file.">  
    <IPermission class="FileIOPermission"  
       version="1"  
       Read="C:\MyFile.xml"/>  
    <IPermission class="SecurityPermission"  
       version="1"  
       Flags="Assertion, Execution"/>  
</PermissionSet>  
```  
  
 <span data-ttu-id="973ae-147">이 권한 집합을 부여하는 코드 그룹은 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="973ae-147">A code group that you grant this permission set might look like the following:</span></span>  
  
```  
<CodeGroup class="UnionCodeGroup"  
   version="1"  
   PermissionSetName="MyNewFilePermissionSet"  
   Name="MyNewCodeGroup"  
   Description="A special code group for my custom assembly.">  
   <IMembershipCondition class="UrlMembershipCondition"  
      version="1"  
      Url="C:\Program Files\Microsoft SQL Server\MSRS10_50.MSSQLSERVER\Reporting Services\ReportServer\bin\MyCustomAssembly.dll"/>  
</CodeGroup>  
```  
  
## <a name="see-also"></a><span data-ttu-id="973ae-148">참고 항목</span><span class="sxs-lookup"><span data-stu-id="973ae-148">See Also</span></span>  
 [<span data-ttu-id="973ae-149">안전한 개발&#40;Reporting Services&#41;</span><span class="sxs-lookup"><span data-stu-id="973ae-149">Secure Development &#40;Reporting Services&#41;</span></span>](secure-development-reporting-services.md)  
  
  
