---
title: 오류 및 경고 처리 (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- errors [XML for Analysis]
- inline errors [XMLA]
- SOAP faults [XML for Analysis]
- XML for Analysis, errors
- faults [XML for Analysis]
- messages [XML for Analysis]
- XMLA, errors
- warnings [XML for Analysis]
- inline warnings [XMLA]
ms.assetid: ab895282-098d-468e-9460-032598961f45
author: minewiskan
ms.author: owend
ms.openlocfilehash: 07b88d800237e5b4b06af0c1ff11cbd0af846600
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87649771"
---
# <a name="handling-errors-and-warnings-xmla"></a><span data-ttu-id="d4048-102">오류 및 경고 처리(XMLA)</span><span class="sxs-lookup"><span data-stu-id="d4048-102">Handling Errors and Warnings (XMLA)</span></span>
  <span data-ttu-id="d4048-103">XML for Analysis (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) 또는 [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) 메서드 호출을 실행 하지 않거나, 성공적으로 실행 되었으나 오류 또는 경고를 생성 하거나, 성공적으로 실행 되었지만 오류가 포함 된 결과를 반환 하는 경우 오류 처리가 필요 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-103">Error handling is required when an XML for Analysis (XMLA) [Discover](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-discover) or [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute) method call does not run, runs successfully but generates errors or warnings, or runs successfully but returns results that contain errors.</span></span>  
  
|<span data-ttu-id="d4048-104">오류</span><span class="sxs-lookup"><span data-stu-id="d4048-104">Error</span></span>|<span data-ttu-id="d4048-105">보고</span><span class="sxs-lookup"><span data-stu-id="d4048-105">Reporting</span></span>|  
|-----------|---------------|  
|<span data-ttu-id="d4048-106">XMLA 메서드 호출이 실행되지 않음</span><span class="sxs-lookup"><span data-stu-id="d4048-106">The XMLA method call does not run</span></span>|[!INCLUDE[msCoName](../../includes/msconame-md.md)]<span data-ttu-id="d4048-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 오류의 세부 정보를 포함 하는 SOAP 오류 메시지를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns a SOAP fault message that contains the details of the failure.</span></span><br /><br /> <span data-ttu-id="d4048-108">자세한 내용은 [SOAP 오류 처리](#handling_soap_faults)섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4048-108">For more information, see the section, [Handling SOAP Faults](#handling_soap_faults).</span></span>|  
|<span data-ttu-id="d4048-109">메서드 호출이 성공적으로 실행되었으나 오류 또는 경고 발생</span><span class="sxs-lookup"><span data-stu-id="d4048-109">Errors or warnings on a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d4048-110">에는 메서드 호출의 결과를 포함 하는 [루트](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) 요소의 [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) 속성에 각 오류 또는 경고에 대 한 [오류](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) 또는 [경고](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) 요소가 각각 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-110">includes an [error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla) or [warning](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/warning-element-xmla) element for each error or warning, respectively, in the [Messages](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla) property of the [root](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla) element that contains the results of the method call.</span></span><br /><br /> <span data-ttu-id="d4048-111">자세한 내용은 [오류 및 경고 처리](#handling_errors_and_warnings)섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4048-111">For more information, see the section, [Handling Errors and Warnings](#handling_errors_and_warnings).</span></span>|  
|<span data-ttu-id="d4048-112">메서드 호출이 성공적으로 실행되었으나 결과에 오류가 있음</span><span class="sxs-lookup"><span data-stu-id="d4048-112">Errors in the result for a successful method call</span></span>|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d4048-113">`error` `warning` 에는 각각 오류 또는 경고에 대 한 인라인 또는 요소가 메서드 호출 결과의 해당 [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) 또는 [row](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) 요소 내에 포함 되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-113">includes an inline `error` or `warning` element for the error or warning, respectively, within the appropriate [Cell](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/cell-element-xmla) or [row](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/row-element-xmla) element of the results of the method call.</span></span><br /><br /> <span data-ttu-id="d4048-114">자세한 내용은 [인라인 오류 및 경고 처리](#handling_inline_errors_and_warnings)섹션을 참조 하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4048-114">For more information, see the section, [Handling Inline Errors and Warnings](#handling_inline_errors_and_warnings).</span></span>|  
  
##  <a name="handling-soap-faults"></a><a name="handling_soap_faults"></a><span data-ttu-id="d4048-115">SOAP 오류 처리</span><span class="sxs-lookup"><span data-stu-id="d4048-115">Handling SOAP Faults</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d4048-116">에서 SOAP 오류가 반환되는 경우는 다음과 같습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-116">returns a SOAP fault when the following situations occur:</span></span>  
  
-   <span data-ttu-id="d4048-117">XMLA 메서드가 포함된 SOAP 메시지가 올바른 형식이 아니거나 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 해당 메시지의 유효성을 확인할 수 없는 경우</span><span class="sxs-lookup"><span data-stu-id="d4048-117">The SOAP message that contains the XMLA method was not well-formed or could not be validated by the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
-   <span data-ttu-id="d4048-118">XMLA 메서드가 포함된 SOAP 메시지와 관련된 통신 또는 기타 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="d4048-118">A communications or other error occurred involving the SOAP message that contains the XMLA method.</span></span>  
  
-   <span data-ttu-id="d4048-119">XMLA 메서드가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 실행되지 않은 경우</span><span class="sxs-lookup"><span data-stu-id="d4048-119">The XMLA method did not run on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance.</span></span>  
  
 <span data-ttu-id="d4048-120">XMLstartA에 대한 SOAP 오류 코드는 "XMLForAnalysis"로 시작하며 그 뒤에 마침표와 16진수 HRESULT 결과 코드가 붙습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-120">The SOAP fault codes for XMLstartA start with "XMLForAnalysis", followed by a period and the hexadecimal HRESULT result code.</span></span> <span data-ttu-id="d4048-121">예를 들어 오류 코드 "`0x80000005`"는 "`XMLForAnalysis.0x80000005`"가 됩니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-121">For example, an error code of "`0x80000005`" is formatted as "`XMLForAnalysis.0x80000005`".</span></span> <span data-ttu-id="d4048-122">SOAP 오류 형식에 대한 자세한 내용은 W3C SOAP(Simple Object Access Protocol) 1.1에서 Soap Fault를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="d4048-122">For more information about the SOAP fault format, see Soap Fault in the W3C Simple Object Access Protocol (SOAP) 1.1.</span></span>  
  
### <a name="fault-code-information"></a><span data-ttu-id="d4048-123">오류 코드 정보</span><span class="sxs-lookup"><span data-stu-id="d4048-123">Fault Code Information</span></span>  
 <span data-ttu-id="d4048-124">다음 표에서는 SOAP 응답의 세부 정보 섹션에 포함된 XMLA 오류 코드 정보를 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-124">The following table shows the XMLA fault code information that is contained in the detail section of the SOAP response.</span></span> <span data-ttu-id="d4048-125">열은 SOAP 오류의 세부 정보 섹션에 포함된 오류의 특성을 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-125">The columns are the attributes of an error in the detail section of a SOAP fault.</span></span>  
  
|<span data-ttu-id="d4048-126">열 이름</span><span class="sxs-lookup"><span data-stu-id="d4048-126">Column name</span></span>|<span data-ttu-id="d4048-127">Type</span><span class="sxs-lookup"><span data-stu-id="d4048-127">Type</span></span>|<span data-ttu-id="d4048-128">Description</span><span class="sxs-lookup"><span data-stu-id="d4048-128">Description</span></span>|<span data-ttu-id="d4048-129">Null 허용<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="d4048-129">Null allowed<sup>1</sup></span></span>|  
|-----------------|----------|-----------------|------------------------------|  
|`ErrorCode`|`UnsignedInt`|<span data-ttu-id="d4048-130">메서드의 성공 또는 실패를 나타내는 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-130">Return code that indicates the success or failure of the method.</span></span> <span data-ttu-id="d4048-131">16진수 값은 `UnsignedInt` 값으로 변환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-131">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="d4048-132">아니요</span><span class="sxs-lookup"><span data-stu-id="d4048-132">No</span></span>|  
|`WarningCode`|`UnsignedInt`|<span data-ttu-id="d4048-133">경고 조건을 나타내는 코드를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-133">Return code that indicates a warning condition.</span></span> <span data-ttu-id="d4048-134">16진수 값은 `UnsignedInt` 값으로 변환되어야 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-134">The hexadecimal value must be converted to an `UnsignedInt` value.</span></span>|<span data-ttu-id="d4048-135">예</span><span class="sxs-lookup"><span data-stu-id="d4048-135">Yes</span></span>|  
|`Description`|`String`|<span data-ttu-id="d4048-136">오류가 발생한 구성 요소에서 반환한 오류 또는 경고에 대한 텍스트와 설명입니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-136">Error or warning text and description returned by the component that generated the error.</span></span>|<span data-ttu-id="d4048-137">예</span><span class="sxs-lookup"><span data-stu-id="d4048-137">Yes</span></span>|  
|`Source`|`String`|<span data-ttu-id="d4048-138">오류 또는 경고가 발생한 구성 요소의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-138">Name of the component that generated the error or warning.</span></span>|<span data-ttu-id="d4048-139">예</span><span class="sxs-lookup"><span data-stu-id="d4048-139">Yes</span></span>|  
|`HelpFile`|`String`|<span data-ttu-id="d4048-140">오류 또는 경고를 설명하는 도움말 파일 또는 항목의 경로 또는 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-140">Path or URL to the Help file or topic that describes the error or warning.</span></span>|<span data-ttu-id="d4048-141">예</span><span class="sxs-lookup"><span data-stu-id="d4048-141">Yes</span></span>|  
  
 <span data-ttu-id="d4048-142"><sup>1</sup> 은 데이터가 필수이 고 반환 되어야 하는지 여부 또는 데이터가 선택적 이며 열이 적용 되지 않는 경우 null 문자열이 허용 되는지 여부를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-142"><sup>1</sup> Indicates whether the data is required and must be returned, or whether the data is optional and a null string is allowed if the column does not apply.</span></span>  
  
 <span data-ttu-id="d4048-143">다음은 메서드 호출이 실패했을 때 발생하는 SOAP 오류 예입니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-143">The following is an example of a SOAP fault that occurred when a method call failed:</span></span>  
  
```  
<?xml version="1.0"?>  
   <SOAP-ENV:Envelope  
   xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/"  
   SOAP-ENV:encodingStyle="http://schemas.xmlsoap.org/soap/encoding/">  
      <SOAP-ENV:Fault>  
         <faultcode>XMLAnalysisError.0x80000005</faultcode>  
         <faultstring>The XML for Analysis provider encountered an error.</faultstring>  
         <faultactor>XML for Analysis Provider</faultactor>  
         <detail>  
<Error  
ErrorCode="2147483653"  
Description="An unexpected error has occurred."  
Source="XML for Analysis Provider"  
HelpFile="" />  
         </detail>  
      </SOAP-ENV:Fault>  
</SOAP-ENV:Envelope>  
```  
  
##  <a name="handling-errors-and-warnings"></a><a name="handling_errors_and_warnings"></a><span data-ttu-id="d4048-144">오류 및 경고 처리</span><span class="sxs-lookup"><span data-stu-id="d4048-144">Handling Errors and Warnings</span></span>  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d4048-145">에서는 명령 실행 후 다음과 같은 상황이 발생할 경우 명령에 대한 `Messages` 요소에 `root` 속성을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-145">returns the `Messages` property in the `root` element for a command if the following situations occur after that command runs:</span></span>  
  
-   <span data-ttu-id="d4048-146">메서드 자체는 실패하지 않았지만 메서드가 성공적으로 호출된 후 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 오류가 발생한 경우</span><span class="sxs-lookup"><span data-stu-id="d4048-146">The method itself did not fail, but a failure occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the method call succeeded.</span></span>  
  
-   <span data-ttu-id="d4048-147">명령을 성공적으로 실행했지만 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 경고를 반환한 경우</span><span class="sxs-lookup"><span data-stu-id="d4048-147">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance returns a warning when the command is successful.</span></span>  
  
 <span data-ttu-id="d4048-148">`Messages` 속성은 `root` 요소에 포함된 속성 중 마지막 속성이며 `Message` 요소를 한 개 이상 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-148">The `Messages` property follows all other properties that are contained by the `root` element, and can contain one or more `Message` elements.</span></span> <span data-ttu-id="d4048-149">또한 각 `Message` 요소는 지정된 명령에 대해 발생한 오류나 경고를 설명하는 단일 `error` 또는 `warning` 요소를 포함할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-149">In turn, each `Message` element can contain either a single `error` or `warning` element describing any errors or warnings, respectively, that occurred for the specified command.</span></span>  
  
 <span data-ttu-id="d4048-150">속성에 포함 된 오류 및 경고에 대 한 자세한 내용은 `Messages` [Messages 요소 &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla)를 참조 하세요.</span><span class="sxs-lookup"><span data-stu-id="d4048-150">For more information about errors and warnings that are contained in the `Messages` property, see [Messages Element &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/messages-element-xmla).</span></span>  
  
### <a name="handling-errors-during-serialization"></a><span data-ttu-id="d4048-151">직렬화 중 오류 해결</span><span class="sxs-lookup"><span data-stu-id="d4048-151">Handling Errors During Serialization</span></span>  
 <span data-ttu-id="d4048-152">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]인스턴스가 성공적으로 실행 된 명령의 출력을 직렬화 한 후에 오류가 발생 하는 경우는 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 오류 지점에서 다른 네임 스페이스의 [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) 요소를 반환 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-152">If an error occurs after the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance has already begun serializing the output of a successfully run command, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an [Exception](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/exception-element-xmla) element in a different namespace at the point of the error.</span></span> <span data-ttu-id="d4048-153">그러면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스는 클라이언트에 보낸 XML 문서가 유효한 문서가 되도록 열려 있는 요소를 모두 닫습니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-153">The [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance then closes all open elements so that the XML document sent to the client is a valid document.</span></span> <span data-ttu-id="d4048-154">또한 오류에 대한 설명이 들어 있는 `Messages` 요소도 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-154">The instance also returns a `Messages` element that contains the description of the error.</span></span>  
  
##  <a name="handling-inline-errors-and-warnings"></a><a name="handling_inline_errors_and_warnings"></a><span data-ttu-id="d4048-155">인라인 오류 및 경고 처리</span><span class="sxs-lookup"><span data-stu-id="d4048-155">Handling Inline Errors and Warnings</span></span>  
 <span data-ttu-id="d4048-156">XMLA 메서드 자체는 실패하지 않았지만 XMLA 메서드가 성공적으로 호출된 후 반환된 결과의 데이터 요소와 관련된 오류가 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 인스턴스에서 발생하면 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]에서는 명령에 대한 인라인 `error` 또는 `warning`을 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-156">[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an inline `error` or `warning` for a command if the XMLA method itself did not fail, but an error specific to a data element in the results returned by the method occurred on the [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] instance after the XMLA method call succeeded.</span></span>  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]<span data-ttu-id="d4048-157">`error` `warning` `root` [mddataset](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) 데이터 형식을 사용 하 여 요소 내에 포함 된 셀 또는 다른 데이터에 대해 발생 하는 문제 (예: 보안 오류 또는 셀 형식 지정 오류)가 발생 하는 경우 인라인 및 요소를 제공 합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-157">supplies inline `error` and `warning` elements if issues specific to a cell or to other data that are contained within a `root` element using the [MDDataSet](https://docs.microsoft.com/bi-reference/xmla/xml-data-types/mddataset-data-type-xmla) data type occur, such as a security error or formatting error for a cell.</span></span> <span data-ttu-id="d4048-158">이러한 경우 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]는 오류 또는 경고가 포함된 `error` 또는 `warning` 요소에 `Cell` 또는 `row` 요소를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-158">In these cases, [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] returns an `error` or `warning` element in the `Cell` or `row` element that contains the error or warning, respectively.</span></span>  
  
 <span data-ttu-id="d4048-159">다음 예에서는 `Execute` [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) 명령을 사용 하 여 메서드에서 반환 된 행 집합에 오류가 포함 된 결과 집합을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="d4048-159">The following example illustrates a result set that contains an error in the rowset returned from an `Execute` method using the [Statement](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/statement-element-xmla) command.</span></span>  
  
```  
<return>  
   ...  
   <root>  
      ...  
      <CellData>  
      ...  
         <Cell CellOrdinal="10">  
            <Value>  
               <Error>  
                  <ErrorCode>2148497527</ErrorCode>   
                  <Description>Security Error.</Description>   
               </Error>  
            </Value>  
         </Cell>  
      </CellData>  
      ...  
   </root>  
   ...  
</return>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4048-160">참고 항목</span><span class="sxs-lookup"><span data-stu-id="d4048-160">See Also</span></span>  
 [<span data-ttu-id="d4048-161">Analysis Services에서 XMLA를 사용하여 개발</span><span class="sxs-lookup"><span data-stu-id="d4048-161">Developing with XMLA in Analysis Services</span></span>](developing-with-xmla-in-analysis-services.md)  
  
  
