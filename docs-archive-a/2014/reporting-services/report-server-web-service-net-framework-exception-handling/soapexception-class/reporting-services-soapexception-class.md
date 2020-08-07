---
title: Reporting Services SoapException 클래스 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- exceptions [Reporting Services], SoapException class
- SoapException class
ms.assetid: 2cec49ee-20b1-40eb-a75b-0908d9c05b34
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 6f6efdfac89014116957990ef2db21cf52e76a4f
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87731415"
---
# <a name="reporting-services-soapexception-class"></a><span data-ttu-id="1d4d4-102">Reporting Services SoapException 클래스</span><span class="sxs-lookup"><span data-stu-id="1d4d4-102">Reporting Services SoapException Class</span></span>
  <span data-ttu-id="1d4d4-103">발생할 수 있다고 판단되는 특정 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 오류를 해결해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-103">You should address specific [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] errors that you know might happen.</span></span> <span data-ttu-id="1d4d4-104">예를 들어, 사용자에게 폴더를 만들도록 요구하는 애플리케이션에서 사용자는 이미 존재하는 폴더를 만들려고 시도할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-104">For example, in an application where you ask the user to create a folder, it might be possible for the user to try to create a folder that already exists.</span></span> <span data-ttu-id="1d4d4-105">개발자는 사용자가 애플리케이션의 폴더 이름 및 경로 필드에 입력하는 내용을 제어하지 못하지만, 누군가가 실수로 이미 존재하는 항목을 만들려고 시도할 때 발생하는 사용자 경험은 제어할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-105">As the developer, you do not have control over what the user enters in the folder name and path fields of your application, but you do have control over what the user experience is when someone incidentally tries to create an item that already exists.</span></span>  
  
 <span data-ttu-id="1d4d4-106">특정 오류 조건을 쉽게 파악할 수 있도록 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]은 예외에 대한 오류 코드를 분류하고 **SoapException** 클래스의 속성을 사용하여 오류에 대한 분류를 반환합니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-106">To make it easier for you to catch specific error conditions, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] classifies an error code for the exception and returns the classification of the error using properties from the **SoapException** class.</span></span> <span data-ttu-id="1d4d4-107">자세한 내용은 SDK 설명서의 "SoapException 클래스"를 참조 하십시오 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="1d4d4-107">For more information, see "SoapException Class" in the [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK documentation.</span></span>  
  
 <span data-ttu-id="1d4d4-108">다음 표는 **SoapException** 클래스의 공용 속성을 나열합니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-108">The following table lists the public properties of the **SoapException** class.</span></span>  
  
|<span data-ttu-id="1d4d4-109">공용 속성</span><span class="sxs-lookup"><span data-stu-id="1d4d4-109">Public property</span></span>|<span data-ttu-id="1d4d4-110">설명</span><span class="sxs-lookup"><span data-stu-id="1d4d4-110">Description</span></span>|  
|---------------------|-----------------|  
|<span data-ttu-id="1d4d4-111">**배우**</span><span class="sxs-lookup"><span data-stu-id="1d4d4-111">**Actor**</span></span>|<span data-ttu-id="1d4d4-112">예외를 발생시킨 코드입니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-112">The code that caused the exception.</span></span> <span data-ttu-id="1d4d4-113">값은 웹 서비스 메서드에 대한 URL입니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-113">The value is the URL to the Web service method.</span></span>|  
|<span data-ttu-id="1d4d4-114">**세부 정보**</span><span class="sxs-lookup"><span data-stu-id="1d4d4-114">**Detail**</span></span>|<span data-ttu-id="1d4d4-115">애플리케이션별 오류 정보입니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-115">Application-specific error information.</span></span> <span data-ttu-id="1d4d4-116">값은 보고서 서버에서 설정되며 XML 형식입니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-116">The value is set by the report server and is in XML format.</span></span> <span data-ttu-id="1d4d4-117">자세한 내용은 참조 [Detail 속성](detail-property.md) 및 [Detail 속성을 사용하여 특정 오류 처리](../best-practices/using-the-detail-property-to-handle-specific-errors.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-117">For more information, see [Detail Property](detail-property.md) and [Using the Detail Property to Handle Specific Errors](../best-practices/using-the-detail-property-to-handle-specific-errors.md).</span></span>|  
|<span data-ttu-id="1d4d4-118">**HelpLink**</span><span class="sxs-lookup"><span data-stu-id="1d4d4-118">**HelpLink**</span></span>|<span data-ttu-id="1d4d4-119">오류와 연관된 도움말 파일에 대한 URL 또는 URN입니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-119">A URL or URN to a Help file associated with the error.</span></span> <span data-ttu-id="1d4d4-120">일반적으로 웹 서비스에서 설정되는 이 값은 URL을 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] 도움말 및 지원으로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-120">The value is usually set by the Web service and it sets a URL to [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Help and Support.</span></span> <span data-ttu-id="1d4d4-121">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]는 발생하는 오류와 관련하여 여러 도움말 링크를 지원하므로 보고서 서버에서는 도움말 링크 정보를 **Detail** 속성의 일부로 설정합니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-121">Because [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] supports multiple help links for errors that occur, the report server sets help link information as part of the **Detail** property.</span></span> <span data-ttu-id="1d4d4-122">자세한 내용은 [HelpLink 요소](helplink-element.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-122">For more information, see [HelpLink Element](helplink-element.md).</span></span>|  
|<span data-ttu-id="1d4d4-123">**Message**</span><span class="sxs-lookup"><span data-stu-id="1d4d4-123">**Message**</span></span>|<span data-ttu-id="1d4d4-124">오류를 설명하는 지역화된 메시지입니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-124">A descriptive, localized message that describes the error.</span></span> <span data-ttu-id="1d4d4-125">이 텍스트는 애플리케이션 UI로 나타날 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="1d4d4-125">This text might appear in the application UI.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d4d4-126">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1d4d4-126">See Also</span></span>  
 <span data-ttu-id="1d4d4-127">[Reporting Services에서 예외 처리 소개](../introducing-exception-handling-in-reporting-services.md) </span><span class="sxs-lookup"><span data-stu-id="1d4d4-127">[Introducing Exception Handling in Reporting Services](../introducing-exception-handling-in-reporting-services.md) </span></span>  
 [<span data-ttu-id="1d4d4-128">SoapException 오류 테이블</span><span class="sxs-lookup"><span data-stu-id="1d4d4-128">SoapException Errors Table</span></span>](soapexception-errors-table.md)  
  
  
