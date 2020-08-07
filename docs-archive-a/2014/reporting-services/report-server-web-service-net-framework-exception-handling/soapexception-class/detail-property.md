---
title: Detail 속성 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- Detail property
- SoapException class
ms.assetid: c1ddaeb6-c540-49fa-b06e-b6359d377ee8
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 060fbaba2b8d4f5a5171e8aa7995432622ba2ba0
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87734999"
---
# <a name="detail-property"></a><span data-ttu-id="a1646-102">Detail 속성</span><span class="sxs-lookup"><span data-stu-id="a1646-102">Detail Property</span></span>
  <span data-ttu-id="a1646-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException**클래스의 **Detail** 속성은 다음 XML 구조를 가집니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-103">The **Detail** property of the [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] **SoapException** class has the following XML structure:</span></span>  
  
## <a name="elements"></a><span data-ttu-id="a1646-104">요소</span><span class="sxs-lookup"><span data-stu-id="a1646-104">Elements</span></span>  
 <span data-ttu-id="a1646-105">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="a1646-105">**Detail**</span></span>  
 <span data-ttu-id="a1646-106">모든 기타 오류 세부 정보 요소를 포함하는 최상위 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-106">The top-level element that contains all other error detail elements.</span></span>  
  
 <span data-ttu-id="a1646-107">**ErrorCode**</span><span class="sxs-lookup"><span data-stu-id="a1646-107">**ErrorCode**</span></span>  
 <span data-ttu-id="a1646-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 특정 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-108">The [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]-specific error code.</span></span>  
  
 <span data-ttu-id="a1646-109">**HttpStatus**</span><span class="sxs-lookup"><span data-stu-id="a1646-109">**HttpStatus**</span></span>  
 <span data-ttu-id="a1646-110">HTTP 상태 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-110">The HTTP status code.</span></span>  
  
 <span data-ttu-id="a1646-111">**Message**</span><span class="sxs-lookup"><span data-stu-id="a1646-111">**Message**</span></span>  
 <span data-ttu-id="a1646-112">보고서 서버에서 할당한 오류 메시지 및 오류 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-112">The error message and the error code assigned by the report server.</span></span>  
  
 <span data-ttu-id="a1646-113">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="a1646-113">**HelpLink**</span></span>  
 <span data-ttu-id="a1646-114">오류에 대한 추가 정보를 찾을 수 있는 웹 사이트에 대한 도움말 링크 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-114">The Help link URL to a Web site at which further information about the error can be found.</span></span> <span data-ttu-id="a1646-115">자세한 내용은 [HelpLink 요소](helplink-element.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="a1646-115">For more information, see [HelpLink Element](helplink-element.md).</span></span>  
  
 <span data-ttu-id="a1646-116">**LinkID**</span><span class="sxs-lookup"><span data-stu-id="a1646-116">**LinkID**</span></span>  
 <span data-ttu-id="a1646-117">링크에 할당된 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-117">The ID assigned to the link.</span></span>  
  
 <span data-ttu-id="a1646-118">**제품**</span><span class="sxs-lookup"><span data-stu-id="a1646-118">**ProductName**</span></span>  
 <span data-ttu-id="a1646-119">제품의 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-119">The name of the product.</span></span> <span data-ttu-id="a1646-120">기본값은 **Microsoft SQL Server Reporting Services**입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-120">The default value is **Microsoft SQL Server Reporting Services**.</span></span>  
  
 <span data-ttu-id="a1646-121">**ProductVersion**</span><span class="sxs-lookup"><span data-stu-id="a1646-121">**ProductVersion**</span></span>  
 <span data-ttu-id="a1646-122">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]의 버전입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-122">The version of [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span> <span data-ttu-id="a1646-123">최대 길이는 15자입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-123">The maximum length is 15 characters.</span></span> <span data-ttu-id="a1646-124">버전 번호의 형식은 8.00.0xxx.00과 같아야 합니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-124">The format of the version number should be as follows: 8.00.0xxx.00.</span></span>  
  
 <span data-ttu-id="a1646-125">**ProductLocaleId**</span><span class="sxs-lookup"><span data-stu-id="a1646-125">**ProductLocaleId**</span></span>  
 <span data-ttu-id="a1646-126">애플리케이션 INTL DLL의 로캘 ID 또는 언어 ID입니다(예: 0x41A).</span><span class="sxs-lookup"><span data-stu-id="a1646-126">The locale ID or language ID of the application's INTL DLL (for example, 0x41A).</span></span>  
  
 <span data-ttu-id="a1646-127">**OperatingSystem**</span><span class="sxs-lookup"><span data-stu-id="a1646-127">**OperatingSystem**</span></span>  
 <span data-ttu-id="a1646-128">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]가 설치된 운영 체제입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-128">The operating system [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] is installed on.</span></span> <span data-ttu-id="a1646-129">유효한 값은 운영 체제에 대해 독립적인 경우 **0**, [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)]의 경우 **1**, Windows XP의 경우 **16**입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-129">Valid values include **0** for operating system independent, **1** for [!INCLUDE[win2kfamily](../../../includes/win2kfamily-md.md)], and **16** for Windows XP.</span></span>  
  
 <span data-ttu-id="a1646-130">**CountryLocaleId**</span><span class="sxs-lookup"><span data-stu-id="a1646-130">**CountryLocaleId**</span></span>  
 <span data-ttu-id="a1646-131">운영 체제의 로캘 ID 또는 언어 ID입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-131">The locale ID or language ID of the operating system.</span></span> <span data-ttu-id="a1646-132">예를 들어 프랑스어 버전 Windows에 대해 이 값은 0x040c입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-132">For example, the value for the French version of Windows is 0x040c.</span></span>  
  
 <span data-ttu-id="a1646-133">**MoreInformation**</span><span class="sxs-lookup"><span data-stu-id="a1646-133">**MoreInformation**</span></span>  
 <span data-ttu-id="a1646-134">메서드 실행 중 발생한 중첩된 예외를 포함하는 XML 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-134">An XML string that contains nested exceptions that occurred while the method ran.</span></span>  
  
 <span data-ttu-id="a1646-135">**원본**</span><span class="sxs-lookup"><span data-stu-id="a1646-135">**Source**</span></span>  
 <span data-ttu-id="a1646-136">**MoreInformation**의 자식 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-136">A child element of **MoreInformation**.</span></span> <span data-ttu-id="a1646-137">오류의 출처입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-137">The source of the error.</span></span>  
  
 <span data-ttu-id="a1646-138">**Message**</span><span class="sxs-lookup"><span data-stu-id="a1646-138">**Message**</span></span>  
 <span data-ttu-id="a1646-139">**MoreInformation**의 자식 요소입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-139">A child element of **MoreInformation**.</span></span> <span data-ttu-id="a1646-140">중첩된 예외의 오류 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-140">The error message of a nested exception.</span></span> <span data-ttu-id="a1646-141">이 요소에는 **ErrorCode** 및 **HelpLink**에 대한 XML 요소가 포함됩니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-141">This element includes XML attributes for **ErrorCode** and **HelpLink**.</span></span>  
  
 <span data-ttu-id="a1646-142">**경고**</span><span class="sxs-lookup"><span data-stu-id="a1646-142">**Warnings**</span></span>  
 <span data-ttu-id="a1646-143">보고서 처리에서 반환된 경고를 포함하는 XML 문자열입니다.</span><span class="sxs-lookup"><span data-stu-id="a1646-143">An XML string that contains the warnings returned from report processing.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1646-144">참고 항목</span><span class="sxs-lookup"><span data-stu-id="a1646-144">See Also</span></span>  
 <span data-ttu-id="a1646-145">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="a1646-145">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 <span data-ttu-id="a1646-146">[Reporting Services SoapException 클래스](reporting-services-soapexception-class.md) </span><span class="sxs-lookup"><span data-stu-id="a1646-146">[Reporting Services SoapException Class](reporting-services-soapexception-class.md) </span></span>  
 [<span data-ttu-id="a1646-147">Detail 속성을 사용하여 특정 오류 처리</span><span class="sxs-lookup"><span data-stu-id="a1646-147">Using the Detail Property to Handle Specific Errors</span></span>](../best-practices/using-the-detail-property-to-handle-specific-errors.md)  
  
  
