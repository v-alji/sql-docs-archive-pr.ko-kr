---
title: 배달 확장 프로그램 구현 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- delivery [Reporting Services]
- custom delivery extensions [Reporting Services]
- extensions [Reporting Services], delivery
- delivery extensions [Reporting Services]
ms.assetid: 600cd229-efcd-480e-8c95-3c3c39ff4e7a
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: af1e804e029dae77fb7836577aa8d4a45ad20109
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661556"
---
# <a name="implementing-a-delivery-extension"></a><span data-ttu-id="af450-102">배달 확장 프로그램 구현</span><span class="sxs-lookup"><span data-stu-id="af450-102">Implementing a Delivery Extension</span></span>
  <span data-ttu-id="af450-103">사용자는 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]를 통해 보고서를 만들고 게시한 다음에 다양한 위치로 배달할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af450-103">[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] enables users to create and publish reports that, once created and published, can be delivered to various locations.</span></span> <span data-ttu-id="af450-104">또한 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에는 다수의 배달 확장 프로그램이 포함되어 있으며 개발자가 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]에서 배달 기능을 더욱 확장할 수 있도록 추가 배달 확장 프로그램을 만들 수 있는 배달 API가 포함되어 있습니다.</span><span class="sxs-lookup"><span data-stu-id="af450-104">In addition, [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] includes several delivery extensions and a delivery API that enable developers to create additional delivery extensions to further extend the functionality of delivery in [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 <span data-ttu-id="af450-105">배달 확장 프로그램의 예제 구현은 [SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889)를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="af450-105">For a sample implementation of a delivery extension, see [SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="af450-106">섹션 내용</span><span class="sxs-lookup"><span data-stu-id="af450-106">In This Section</span></span>  
 <span data-ttu-id="af450-107">[배달 확장 프로그램 개요] 배달-확장-overview.md)</span><span class="sxs-lookup"><span data-stu-id="af450-107">[Delivery Extensions Overview]delivery-extensions-overview.md)</span></span>  
 <span data-ttu-id="af450-108">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)]용 사용자 지정 배달 확장 프로그램을 작성하는 방법을 소개합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-108">Introduces how to write a custom delivery extension for [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)].</span></span>  
  
 [<span data-ttu-id="af450-109">배달 확장 프로그램 구현 준비</span><span class="sxs-lookup"><span data-stu-id="af450-109">Preparing to Implement a Delivery Extension</span></span>](preparing-to-implement-a-delivery-extension.md)  
 <span data-ttu-id="af450-110">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 구현할 때 사용할 수 있는 인터페이스와 클래스 및 구현 전에 고려할 사항을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-110">Describes the interfaces and classes available when implementing an [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, as well as issues to consider before implementation.</span></span>  
  
 [<span data-ttu-id="af450-111">배달 확장 프로그램 라이브러리 만들기</span><span class="sxs-lookup"><span data-stu-id="af450-111">Creating a Delivery Extension Library</span></span>](creating-a-delivery-extension-library.md)  
 <span data-ttu-id="af450-112">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램에 대한 네임스페이스 할당에 대해 설명하고 배달 확장 프로그램을 라이브러리 DLL로 컴파일하는 방법에 대해 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-112">Describes assigning a namespace for your [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension and compiling your delivery extension into a library DLL.</span></span>  
  
 [<span data-ttu-id="af450-113">배달 확장 프로그램에 대한 IDeliveryExtension 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="af450-113">Implementing the IDeliveryExtension Interface for a Delivery Extension</span></span>](implementing-the-ideliveryextension-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="af450-114">배달 확장 프로그램의 특성 및 고유의 배달 확장 프로그램 클래스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-114">Describes the attributes of a delivery extension, and how to implement your own delivery extension class.</span></span>  
  
 [<span data-ttu-id="af450-115">배달 확장 프로그램에 대해 Notification 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="af450-115">Using a Notification Class for a Delivery Extension</span></span>](using-a-notification-class-for-a-delivery-extension.md)  
 <span data-ttu-id="af450-116">**Notification** 클래스의 특성 및 이 클래스를 배달 확장 프로그램 구현에서 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-116">Describes the attributes of a **Notification** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="af450-117">배달 확장 프로그램에 대해 Setting 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="af450-117">Using the Setting Class for a Delivery Extension</span></span>](using-the-setting-class-for-a-delivery-extension.md)  
 <span data-ttu-id="af450-118">**Setting** 클래스의 특성 및 이 클래스를 배달 확장 프로그램 구현에서 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-118">Describes the attributes of a **Setting** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="af450-119">배달 확장 프로그램에 대해 IDeliveryReportServerInformation 인터페이스 사용</span><span class="sxs-lookup"><span data-stu-id="af450-119">Using the IDeliveryReportServerInformation Interface for a Delivery Extension</span></span>](using-the-ideliveryreportserverinformation-interface-for-a-delivery-extension.md)  
 <span data-ttu-id="af450-120">**IDeliveryReportServerInformation** 인터페이스의 특성 및 이 인터페이스를 배달 확장 프로그램 구현에서 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-120">Describes the attributes of a **IDeliveryReportServerInformation** interface and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="af450-121">배달 확장 프로그램에 대해 Report 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="af450-121">Using the Report Class for a Delivery Extension</span></span>](using-the-report-class-for-a-delivery-extension.md)  
 <span data-ttu-id="af450-122">**Report** 클래스의 특성 및 이 클래스를 배달 확장 프로그램 구현에서 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-122">Describes the attributes of a **Report** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="af450-123">배달 확장 프로그램에 대해 RenderedOutputFile 클래스 사용</span><span class="sxs-lookup"><span data-stu-id="af450-123">Using the RenderedOutputFile Class for a Delivery Extension</span></span>](using-the-renderedoutputfile-class-for-a-delivery-extension.md)  
 <span data-ttu-id="af450-124">**RenderedOutputFile** 클래스의 특성 및 이 클래스를 배달 확장 프로그램 구현에서 사용하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-124">Describes the attributes of a **RenderedOutputFile** class and how to use it in your delivery extension implementation.</span></span>  
  
 [<span data-ttu-id="af450-125">배달 확장 프로그램에 대한 ISubscriptionBaseUIUserControl 인터페이스 구현</span><span class="sxs-lookup"><span data-stu-id="af450-125">Implementing the ISubscriptionBaseUIUserControl Interface for a Delivery Extension</span></span>](implementing-the-isubscriptionbaseuiusercontrol-interface.md)  
 <span data-ttu-id="af450-126">배달 확장 프로그램 사용자 컨트롤의 특성 및 고유의 구독용 사용자 인터페이스를 구현하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-126">Describes the attributes of a delivery extension user control and how to implement your own user interface for a subscription.</span></span>  
  
 [<span data-ttu-id="af450-127">배달 확장 프로그램 배포</span><span class="sxs-lookup"><span data-stu-id="af450-127">Deploying a Delivery Extension</span></span>](deploying-a-delivery-extension.md)  
 <span data-ttu-id="af450-128">배달 확장 프로그램을 배포하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-128">Describes how to deploy your delivery extension.</span></span>  
  
 [<span data-ttu-id="af450-129">배달 확장 프로그램 코드 디버깅</span><span class="sxs-lookup"><span data-stu-id="af450-129">Debugging Delivery Extension Code</span></span>](debugging-delivery-extension-code.md)  
 <span data-ttu-id="af450-130">배달 확장 프로그램에서 코드를 디버깅하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-130">Describes how to debug code in your delivery extension.</span></span>  
  
 [<span data-ttu-id="af450-131">배달 확장 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="af450-131">Removing a Delivery Extension</span></span>](removing-a-delivery-extension.md)  
 <span data-ttu-id="af450-132">보고서 서버에서 배달 확장 프로그램을 제거하는 방법을 설명합니다.</span><span class="sxs-lookup"><span data-stu-id="af450-132">Describes how to remove a delivery extension from a report server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af450-133">참고 항목</span><span class="sxs-lookup"><span data-stu-id="af450-133">See Also</span></span>  
 <span data-ttu-id="af450-134">[Reporting Services 확장](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="af450-134">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 [<span data-ttu-id="af450-135">Reporting Services 확장 프로그램 라이브러리</span><span class="sxs-lookup"><span data-stu-id="af450-135">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
