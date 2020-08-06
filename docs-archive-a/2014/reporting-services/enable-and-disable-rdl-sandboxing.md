---
title: RDL 샌드박싱 사용 및 사용 안 함 Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: d5619e9f-ec5b-4376-9b34-1f74de6fade7
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7af1477751093862c99d00978278315e600511e7
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87735055"
---
# <a name="enable-and-disable-rdl-sandboxing"></a><span data-ttu-id="9cdd3-102">RDL 샌드박싱 설정 및 해제</span><span class="sxs-lookup"><span data-stu-id="9cdd3-102">Enable and Disable RDL Sandboxing</span></span>
  <span data-ttu-id="9cdd3-103">RDL(Report Definition Language) 샌드박싱 기능을 사용하면 보고서 서버의 단일 웹 팜을 여러 명이 사용하는 환경에서 각 개인에 대해 특정 유형의 리소스 사용을 검색하고 제한할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-103">The RDL (Report Definition Language) Sandboxing feature lets you detect and restrict the usage of specific types of resources, by individual tenants, in an environment of multiple tenants that use a single web farm of report servers.</span></span> <span data-ttu-id="9cdd3-104">여러 명 그리고 경우에 따라 서로 다른 회사에서 사용할 수 있는 보고서 서버의 단일 웹 팜을 유지 관리하는 호스팅 서비스 시나리오를 예로 들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-104">An example of this is a hosting services scenario where you might maintain a single web farm of report servers that are used by multiple tenants, and perhaps different companies.</span></span> <span data-ttu-id="9cdd3-105">보고서 서버 관리자는 이 기능을 설정하여 다음과 같이 할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-105">As a report server administrator, you can enable this feature to help achieve the following objectives:</span></span>  
  
-   <span data-ttu-id="9cdd3-106">외부 리소스 크기를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-106">Restrict external resource sizes.</span></span> <span data-ttu-id="9cdd3-107">외부 리소스에는 이미지, .xslt 파일, 지도 데이터 등이 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-107">External resources include images, .xslt files, and map data.</span></span>  
  
-   <span data-ttu-id="9cdd3-108">보고서를 게시할 때 식 텍스트에 사용되는 형식 및 멤버를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-108">At report publish time, limit types and members that are used in expression text.</span></span>  
  
-   <span data-ttu-id="9cdd3-109">보고서를 처리할 때 식의 반환 값 크기와 텍스트 길이를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-109">At report processing time, limit the length of the text and the size of the return value for expressions.</span></span>  
  
 <span data-ttu-id="9cdd3-110">RDL 샌드박싱 기능이 설정되면 다음 기능을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-110">When RDL Sandboxing is enabled, the following features are disabled:</span></span>  
  
-   <span data-ttu-id="9cdd3-111">보고서 정의의 요소에 있는 사용자 지정 코드 **\<Code>** 입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-111">Custom code in the **\<Code>** element of a report definition.</span></span>  
  
-   <span data-ttu-id="9cdd3-112">[!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] 사용자 지정 보고서 항목을 위한 RDL 이전 버전 호환 모드</span><span class="sxs-lookup"><span data-stu-id="9cdd3-112">RDL backward compatibility mode for [!INCLUDE[ssRSversion2005](../includes/ssrsversion2005-md.md)] custom report items.</span></span>  
  
-   <span data-ttu-id="9cdd3-113">식의 명명된 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9cdd3-113">Named parameters in expressions.</span></span>  
  
 <span data-ttu-id="9cdd3-114">이 항목에서는 `RDLSandboxing` RSReportServer.Config 파일의 <> 요소에 있는 각 요소에 대해 설명 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-114">This topic describes each element in the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span> <span data-ttu-id="9cdd3-115">이 파일을 수정하는 방법은 [Reporting Services 구성 파일 수정&#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-115">For more information about how to modify this file, see [Modify a Reporting Services Configuration File &#40;RSreportserver.config&#41;](report-server/modify-a-reporting-services-configuration-file-rsreportserver-config.md).</span></span> <span data-ttu-id="9cdd3-116">서버 추적 로그는 RDL 샌드박싱 기능과 관련된 작업을 기록합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-116">A server trace log records activity related to the RDL Sandboxing feature.</span></span> <span data-ttu-id="9cdd3-117">추적 로그에 대한 자세한 내용은 [보고서 서버 서비스 추적 로그](report-server/report-server-service-trace-log.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-117">For more information about trace logs, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
## <a name="example-configuration"></a><span data-ttu-id="9cdd3-118">예제 구성</span><span class="sxs-lookup"><span data-stu-id="9cdd3-118">Example Configuration</span></span>  
 <span data-ttu-id="9cdd3-119">다음 예에서는 `RDLSandboxing` RSReportServer.Config 파일의 <> 요소에 대 한 설정 및 예제 값을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-119">The following example shows the settings and example values for the <`RDLSandboxing`> element in the RSReportServer.Config file.</span></span>  
  
```  
<RDLSandboxing>  
   <MaxExpressionLength>5000</MaxExpressionLength>  
   <MaxResourceSize>5000</MaxResourceSize>  
   <MaxStringResultLength>3000</MaxStringResultLength>  
   <MaxArrayResultLength>250</MaxArrayResultLength>  
   <Types>  
      <Allow Namespace="System.Drawing" AllowNew="True">Bitmap</Allow>  
      <Allow Namespace="TypeConverters.Custom" AllowNew="True">*</Allow>  
   </Types>  
   <Members>  
      <Deny>Format</Deny>  
      <Deny>StrDup</Deny>  
   </Members>  
</RDLSandboxing>  
```  
  
## <a name="configuration-settings"></a><span data-ttu-id="9cdd3-120">구성 설정</span><span class="sxs-lookup"><span data-stu-id="9cdd3-120">Configuration Settings</span></span>  
 <span data-ttu-id="9cdd3-121">다음 표에서는 구성 설정 정보를 제공합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-121">The following table provides information about configuration settings.</span></span> <span data-ttu-id="9cdd3-122">설정은 구성 파일에 나타나는 순서로 표시됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-122">Settings are presented in the order in which they appear in the configuration file.</span></span>  
  
|<span data-ttu-id="9cdd3-123">설정</span><span class="sxs-lookup"><span data-stu-id="9cdd3-123">Setting</span></span>|<span data-ttu-id="9cdd3-124">Description</span><span class="sxs-lookup"><span data-stu-id="9cdd3-124">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="9cdd3-125">**MaxExpressionLength**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-125">**MaxExpressionLength**</span></span>|<span data-ttu-id="9cdd3-126">RDL 식에 허용되는 최대 문자 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-126">Maximum number of characters allowed in RDL expressions.</span></span><br /><br /> <span data-ttu-id="9cdd3-127">기본값: 1000</span><span class="sxs-lookup"><span data-stu-id="9cdd3-127">Default: 1000</span></span>|  
|<span data-ttu-id="9cdd3-128">**MaxResourceSize**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-128">**MaxResourceSize**</span></span>|<span data-ttu-id="9cdd3-129">외부 리소스에 허용되는 최대 크기(KB)입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-129">Maximum number of KB allowed for an external resource.</span></span><br /><br /> <span data-ttu-id="9cdd3-130">기본값: 100</span><span class="sxs-lookup"><span data-stu-id="9cdd3-130">Default: 100</span></span>|  
|<span data-ttu-id="9cdd3-131">**MaxStringResultLength**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-131">**MaxStringResultLength**</span></span>|<span data-ttu-id="9cdd3-132">RDL 식의 반환 값에 허용되는 최대 문자 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-132">Maximum number of characters allowed in a return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="9cdd3-133">기본값: 1000</span><span class="sxs-lookup"><span data-stu-id="9cdd3-133">Default: 1000</span></span>|  
|<span data-ttu-id="9cdd3-134">**MaxArrayResultLength**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-134">**MaxArrayResultLength**</span></span>|<span data-ttu-id="9cdd3-135">RDL 식의 배열 반환 값에 허용되는 최대 항목 수입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-135">Maximum number of items allowed in an array return value for an RDL expression.</span></span><br /><br /> <span data-ttu-id="9cdd3-136">기본값: 100</span><span class="sxs-lookup"><span data-stu-id="9cdd3-136">Default: 100</span></span>|  
|<span data-ttu-id="9cdd3-137">**유형**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-137">**Types**</span></span>|<span data-ttu-id="9cdd3-138">RDL 식 내에 허용할 멤버 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-138">The list of members to allow within RDL expressions.</span></span>|  
|<span data-ttu-id="9cdd3-139">**허용**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-139">**Allow**</span></span>|<span data-ttu-id="9cdd3-140">RDL 식에 허용할 형식 또는 형식 집합입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-140">A type or set of types to allow in RDL expressions.</span></span>|  
|<span data-ttu-id="9cdd3-141">**Namespace**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-141">**Namespace**</span></span>|<span data-ttu-id="9cdd3-142">**Allow** 의 특성이며, Value에 적용되는 하나 이상의 형식이 포함된 네임스페이스입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-142">Attribute for **Allow** that is the namespace that contains one or more types that apply to Value.</span></span> <span data-ttu-id="9cdd3-143">이 속성은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-143">This property is case-insensitive.</span></span>|  
|`AllowNew`|<span data-ttu-id="9cdd3-144">**Allow** 의 부울 특성은 형식의 새 인스턴스를 rdl 식 또는 rdl 요소에 만들 수 있는지 여부를 제어 **\<Class>** 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-144">Boolean attribute for **Allow** that controls whether new instances of the type are allowed to be created in RDL expressions or in an RDL **\<Class>** element.</span></span><br /><br /> <span data-ttu-id="9cdd3-145">참고: `RDLSandboxing` 을 사용 하도록 설정 하면의 설정에 관계 없이 새 배열을 RDL 식에 만들 수 없습니다 `AllowNew` .</span><span class="sxs-lookup"><span data-stu-id="9cdd3-145">Note: When `RDLSandboxing` is enabled, new arrays cannot be created in RDL expressions, regardless of the setting of `AllowNew`.</span></span>|  
|<span data-ttu-id="9cdd3-146">**값**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-146">**Value**</span></span>|<span data-ttu-id="9cdd3-147">**Allow** 의 값이며, RDL 식에 허용할 형식의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-147">Value for **Allow** that is the name of the type to allow in RDL expressions.</span></span> <span data-ttu-id="9cdd3-148">값은 **\*** 네임 스페이스의 모든 형식이 허용 됨을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-148">The value **\*** indicates that all types in the namespace are allowed.</span></span> <span data-ttu-id="9cdd3-149">이 속성은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-149">This property is case-insensitive.</span></span>|  
|<span data-ttu-id="9cdd3-150">**멤버**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-150">**Members**</span></span>|<span data-ttu-id="9cdd3-151">요소에 포함 된 형식 목록의 경우 **\<Types>** RDL 식에 허용 되지 않는 멤버 이름 목록입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-151">For the list of types that are include in the **\<Types>** element, the list of member names that are not allowed in RDL expressions.</span></span>|  
|<span data-ttu-id="9cdd3-152">**Deny**</span><span class="sxs-lookup"><span data-stu-id="9cdd3-152">**Deny**</span></span>|<span data-ttu-id="9cdd3-153">RDL 식에 허용되지 않는 멤버의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-153">The name of a member that is not allowed in RDL expressions.</span></span> <span data-ttu-id="9cdd3-154">이 속성은 대/소문자를 구분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-154">This property is case-insensitive.</span></span><br /><br /> <span data-ttu-id="9cdd3-155">참고: 멤버에 **Deny** 가 지정되면 모든 형식에 대해 이 이름을 사용하는 멤버가 모두 허용되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-155">Note: When **Deny** is specified for a member, all members with this name for all types are not allowed.</span></span>|  
  
## <a name="working-with-expressions-when-rdl-sandboxing-is-enabled"></a><span data-ttu-id="9cdd3-156">RDL 샌드박싱을 사용하는 경우 식 작업</span><span class="sxs-lookup"><span data-stu-id="9cdd3-156">Working with Expressions when RDL Sandboxing is Enabled</span></span>  
 <span data-ttu-id="9cdd3-157">식에 사용되는 리소스를 관리하기 위해 다음과 같은 방식으로 RDL 샌드박싱 기능을 수정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-157">You can modify the RDL Sandboxing feature to help manage the resources that are used by an expression in the following ways:</span></span>  
  
-   <span data-ttu-id="9cdd3-158">식에 사용되는 문자의 수를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-158">Restrict the number of characters that are used for an expression.</span></span>  
  
-   <span data-ttu-id="9cdd3-159">식에서 반환되는 결과의 크기를 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-159">Restrict the size of the result returned by an expression.</span></span>  
  
-   <span data-ttu-id="9cdd3-160">식에 사용할 수 있는 특정 형식 목록을 허용합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-160">Allow a specific list of types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="9cdd3-161">식에 사용할 수 있는 허용된 형식 목록에 대해 이름별로 멤버 목록을 제한합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-161">Restrict the list of members by name for the list of allowed types that can be used in an expression.</span></span>  
  
-   <span data-ttu-id="9cdd3-162">RDL 샌드박싱 기능을 사용하면 승인된 형식 목록과 거부된 멤버 목록을 만들 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-162">The RDL Sandboxing feature enables you to create a list of approved types and a list of denied members.</span></span> <span data-ttu-id="9cdd3-163">승인된 형식 목록을 허용 목록이라고 하고</span><span class="sxs-lookup"><span data-stu-id="9cdd3-163">The list of approved types is called an allow list.</span></span> <span data-ttu-id="9cdd3-164">거부된 멤버 목록을 차단 목록이라고 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-164">The list of denied members is called a block list.</span></span>  
  
> [!NOTE]  
>  <span data-ttu-id="9cdd3-165">보고서 정의에서 컴퓨터는 식 참조의 각 인스턴스에 대한 형식을 알 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-165">In the report definition, a computer cannot know the type of each instances of an expression reference.</span></span> <span data-ttu-id="9cdd3-166">차단 목록에 멤버를 추가하면 허용 목록에 있는 모든 형식에 대해 해당 이름을 갖는 모든 멤버가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-166">When you add a member to the block list, you are denying all members of that name across all types in the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-167">RDL 식 결과는 런타임에 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-167">RDL expression results are verified at run time.</span></span> <span data-ttu-id="9cdd3-168">RDL 식은 보고서가 게시되면 보고서 정의에서 확인됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-168">RDL expressions are verified in the report definition when the report is published.</span></span> <span data-ttu-id="9cdd3-169">보고서 서버 추적 로그를 모니터링하여 위반 항목이 있는지 확인할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-169">Monitor the report server trace log for violations.</span></span> <span data-ttu-id="9cdd3-170">자세한 내용은 [Report Server Service Trace Log](report-server/report-server-service-trace-log.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-170">For more information, see [Report Server Service Trace Log](report-server/report-server-service-trace-log.md).</span></span>  
  
### <a name="working-with-types"></a><span data-ttu-id="9cdd3-171">형식 사용</span><span class="sxs-lookup"><span data-stu-id="9cdd3-171">Working with Types</span></span>  
 <span data-ttu-id="9cdd3-172">허용 목록에 형식을 추가하면 RDL 식에 액세스하기 위해 다음 진입점을 제어하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-172">When you add a type to the allow list, you are controlling the following entry points to access RDL expressions:</span></span>  
  
-   <span data-ttu-id="9cdd3-173">형식의 정적 멤버</span><span class="sxs-lookup"><span data-stu-id="9cdd3-173">Static members of a type.</span></span>  
  
-   <span data-ttu-id="9cdd3-174">[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` 메서드입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-174">The [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `New` method.</span></span>  
  
-   <span data-ttu-id="9cdd3-175">**\<Classes>** 보고서 정의의 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-175">The **\<Classes>** element in the report definition.</span></span>  
  
-   <span data-ttu-id="9cdd3-176">허용 목록의 형식에 대해 차단 목록에 추가한 멤버</span><span class="sxs-lookup"><span data-stu-id="9cdd3-176">Members that you have added to the block list for a type in the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-177">허용 목록은 다음 진입점을 제어하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-177">The allow list does not control the following entry points:</span></span>  
  
-   <span data-ttu-id="9cdd3-178">보고서 데이터 세트.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-178">Report datasets.</span></span> <span data-ttu-id="9cdd3-179">쿼리에서 반환된 보고서 데이터 세트 필드에는 유효한 RDL 형식이 포함되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-179">Fields in report datasets that are returned from queries might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="9cdd3-180">보고서 매개 변수</span><span class="sxs-lookup"><span data-stu-id="9cdd3-180">Report parameters.</span></span> <span data-ttu-id="9cdd3-181">사용자가 제공한 매개 변수 값에는 유효한 RDL 형식이 포함되었을 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-181">User-supplied parameter values might contain any valid RDL type.</span></span>  
  
-   <span data-ttu-id="9cdd3-182">사용 가능한 형식 중에서 차단 목록에 없는 멤버.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-182">Members of an enabled type that are not in the block list.</span></span> <span data-ttu-id="9cdd3-183">기본적으로 허용 목록에 있는 모든 형식의 모든 멤버는 사용할 수 있도록 설정됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-183">By default, all members of all types in the allow list are enabled.</span></span> <span data-ttu-id="9cdd3-184">그러나 차단 목록에 멤버 이름을 추가하면 허용 목록에 있는 모든 형식에 대해 해당 이름을 갖는 모든 멤버가 거부됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-184">When you add a member name to the block list, you are denying all members with that name across all types that are in the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-185">특정 형식의 멤버를 사용하도록 설정하지만 다른 형식 중에서 같은 이름을 사용하는 멤버는 거부하려면 다음과 같이 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-185">To enable a member of one type but deny a member with the same name for a different type, you must do the following:</span></span>  
  
-   <span data-ttu-id="9cdd3-186">**\<Deny>** 멤버 이름에 대 한 요소를 추가 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-186">Add a **\<Deny>** element for the member name.</span></span>  
  
-   <span data-ttu-id="9cdd3-187">사용하도록 설정할 멤버에 대해 사용자 지정 어셈블리의 클래스에 이름이 다른 프록시 멤버를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-187">Create a proxy member with a different name on a class in a custom assembly for the member that you want to enable.</span></span>  
  
-   <span data-ttu-id="9cdd3-188">새 클래스를 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-188">Add that new class to the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-189">[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 함수를 허용 목록에 추가하려면 Microsoft.VisualBasic 네임스페이스에서 해당하는 형식을 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-189">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework functions to the allow list, add the corresponding types from the Microsoft.VisualBasic namespace to the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-190">[!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 형식 키워드를 허용 목록에 추가하려면 해당하는 CLR 형식을 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-190">To add [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework type keywords to the allow list, add the corresponding CLR type to the allow list.</span></span> <span data-ttu-id="9cdd3-191">예를 들어 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 키워드를 사용 하려면 `Integer` 요소에 다음 XML 조각을 추가 합니다 **\<RDLSandboxing>** .</span><span class="sxs-lookup"><span data-stu-id="9cdd3-191">For example, to use the [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework keyword `Integer`, add the following XML fragment to the **\<RDLSandboxing>** element:</span></span>  
  
```  
<Allow Namespace="System">Int32</Allow>  
```  
  
 <span data-ttu-id="9cdd3-192">일반 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework Null 허용 형식을 허용 목록에 추가하려면 다음과 같이 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-192">To add a generic or a [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type to the allow list, you must do the following:</span></span>  
  
-   <span data-ttu-id="9cdd3-193">일반 또는 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework Null 허용 형식에 대한 프록시 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-193">Create a proxy type for the generic or [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework nullable type.</span></span>  
  
-   <span data-ttu-id="9cdd3-194">새로 만든 프록시 형식을 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-194">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-195">사용자 지정 어셈블리의 형식을 허용 목록에 추가해도 암시적으로 이 어셈블리에 대해 실행 권한이 부여되는 것은 아닙니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-195">Adding a type from a custom assembly to the allow list does not implicitly grant execute permission on the assembly.</span></span> <span data-ttu-id="9cdd3-196">코드 액세스 보안 파일을 명확하게 수정하고 어셈블리에 대한 실행 권한을 제공해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-196">You must specifically modify the code access security file and provide execute permission to your assembly.</span></span> <span data-ttu-id="9cdd3-197">자세한 내용은 [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-197">For more information, see [Code Access Security in Reporting Services](extensions/secure-development/code-access-security-in-reporting-services.md).</span></span>  
  
#### <a name="maintaining-the-deny-list-of-members"></a><span data-ttu-id="9cdd3-198">\<Deny>멤버 목록 유지 관리</span><span class="sxs-lookup"><span data-stu-id="9cdd3-198">Maintaining the \<Deny> List of Members</span></span>  
 <span data-ttu-id="9cdd3-199">허용 목록에 새 형식을 추가하는 경우 다음 목록을 사용하여 멤버의 차단 목록을 업데이트해야 할 시기를 결정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-199">When you add a new type to the allow list, use the following list to determine when you might have to update the block list of members:</span></span>  
  
-   <span data-ttu-id="9cdd3-200">새 형식을 제공하는 버전으로 사용자 지정 어셈블리를 업데이트하는 경우</span><span class="sxs-lookup"><span data-stu-id="9cdd3-200">When you update a custom assembly with a version that introduces new types.</span></span>  
  
-   <span data-ttu-id="9cdd3-201">허용 목록의 형식에 멤버를 추가하는 경우</span><span class="sxs-lookup"><span data-stu-id="9cdd3-201">When you add members to the types in the allow list.</span></span>  
  
-   <span data-ttu-id="9cdd3-202">보고서 서버에서 [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] 를 업데이트하는 경우</span><span class="sxs-lookup"><span data-stu-id="9cdd3-202">When you update the [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] on the report server.</span></span>  
  
-   <span data-ttu-id="9cdd3-203">보고서 서버를 이후 버전의 [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)]로 업그레이드하는 경우</span><span class="sxs-lookup"><span data-stu-id="9cdd3-203">When you upgrade the report server to a later version of [!INCLUDE[ssRSnoversion](../includes/ssrsnoversion-md.md)].</span></span>  
  
-   <span data-ttu-id="9cdd3-204">RDL 형식에 새 멤버가 추가되어 나중 RDL 스키마를 처리하기 위해 보고서 서버를 업데이트하는 경우</span><span class="sxs-lookup"><span data-stu-id="9cdd3-204">When you update a report server to handle a later RDL schema, because new members might have been added to RDL types.</span></span>  
  
### <a name="working-with-operators-and-new"></a><span data-ttu-id="9cdd3-205">연산자 및 New 사용</span><span class="sxs-lookup"><span data-stu-id="9cdd3-205">Working with Operators and New</span></span>  
 <span data-ttu-id="9cdd3-206">기본적으로 `New`를 제외한 [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework 언어 연산자는 항상 허용됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-206">By default, [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework language operators, except for `New`, are always allowed.</span></span> <span data-ttu-id="9cdd3-207">`New`연산자는 요소의 특성에 의해 제어 됩니다 `AllowNew` **\<Allow>** .</span><span class="sxs-lookup"><span data-stu-id="9cdd3-207">The `New` operator is controlled by the `AllowNew` attribute on the **\<Allow>** element.</span></span> <span data-ttu-id="9cdd3-208">기본 컬렉션 접근자 연산자 및 .NET Framework 캐스트 매크로와 같은 다른 언어 연산자 `!` [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] `CInt` 는 항상 허용 됩니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-208">Other language operators, such as the default collection accessor operator `!` and [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] .NET Framework cast macros such as `CInt`, are always allowed.</span></span>  
  
 <span data-ttu-id="9cdd3-209">사용자 지정 연산자를 포함하여 연산자를 차단 목록에 추가하는 것은 지원되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-209">Adding operators to a block list, including custom operators, is not supported.</span></span> <span data-ttu-id="9cdd3-210">형식에 대해 연산자를 실행하려면 다음과 같이 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-210">To exclude operators for a type, you must do the following:</span></span>  
  
-   <span data-ttu-id="9cdd3-211">제외할 연산자를 구현하지 않는 프록시 형식을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-211">Create a proxy type that does not implement the operators that you want to exclude.</span></span>  
  
-   <span data-ttu-id="9cdd3-212">새로 만든 프록시 형식을 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-212">Add the proxy type to the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-213">RDL 식에 새 배열을 만들려면 정의하는 클래스에서 메서드에 배열을 만들고 이 클래스를 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-213">To create a new array in an RDL expression, create the array in a method on a class that you define, and add that class to the allow list.</span></span>  
  
 <span data-ttu-id="9cdd3-214">RDL 식에 새 배열을 만들려면 다음과 같이 해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-214">To create a new array in an RDL expression, you must do the following:</span></span>  
  
-   <span data-ttu-id="9cdd3-215">새 클래스를 정의하고 해당 클래스의 메서드에 배열을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-215">Define a new class and create the array in a method on that class.</span></span>  
  
-   <span data-ttu-id="9cdd3-216">이 클래스를 허용 목록에 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="9cdd3-216">Add the class to the allow list.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdd3-217">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9cdd3-217">See Also</span></span>  
 <span data-ttu-id="9cdd3-218">[Rsreportserver.config 구성 파일](report-server/rsreportserver-config-configuration-file.md) </span><span class="sxs-lookup"><span data-stu-id="9cdd3-218">[RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md) </span></span>  
 [<span data-ttu-id="9cdd3-219">보고서 서버 서비스 추적 로그</span><span class="sxs-lookup"><span data-stu-id="9cdd3-219">Report Server Service Trace Log</span></span>](report-server/report-server-service-trace-log.md)  
  
  
