---
title: 배달 확장 프로그램 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- removing delivery extensions
- deleting delivery extensions
- delivery extensions [Reporting Services], removing
ms.assetid: dcb7caf2-d19a-4bc5-afb3-2b61ad11cac5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7c4320f46b5013b0fa2accbc81792748c2d9f384
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87661548"
---
# <a name="removing-a-delivery-extension"></a><span data-ttu-id="1a699-102">배달 확장 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="1a699-102">Removing a Delivery Extension</span></span>
  <span data-ttu-id="1a699-103">[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 배달 확장 프로그램을 제거하려면 구성 파일에서 배달 확장 프로그램에 대한 **Extension** 요소를 제거하기만 하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a699-103">To remove a [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] delivery extension, simply remove the **Extension** element for your delivery extension from the configuration file.</span></span> <span data-ttu-id="1a699-104">구성 정보를 제거한 후에는 보고서 서버에서 배달 확장 프로그램을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="1a699-104">After the configuration information is removed, the delivery extension is no longer available to the report server.</span></span>  
  
 <span data-ttu-id="1a699-105">배달 확장 프로그램의 해당하는 **Extension** 요소가 구성 파일에서 제거되면 배달 확장 프로그램이 더 이상 보고서 서버에 등록되지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="1a699-105">Once a delivery extension's corresponding **Extension** element is removed from the configuration file, it is no longer registered with the report server.</span></span> <span data-ttu-id="1a699-106">보고서 서버는 배달 확장 프로그램 목록에서 항목을 제거하고 해당 배달 확장 프로그램을 사용하는 구독을 비활성화합니다.</span><span class="sxs-lookup"><span data-stu-id="1a699-106">The report server removes the entry from the list of delivery extensions and deactivates any subscriptions which use that delivery extension.</span></span> <span data-ttu-id="1a699-107">배달 확장 프로그램이 제거되면 사용자가 이 프로그램을 알림 방법으로 선택할 수 없게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="1a699-107">When a delivery extension is removed, users are no longer able to select it as a method of notification.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a699-108">참고 항목</span><span class="sxs-lookup"><span data-stu-id="1a699-108">See Also</span></span>  
 <span data-ttu-id="1a699-109">[배달 확장 프로그램 구현](implementing-a-delivery-extension.md) </span><span class="sxs-lookup"><span data-stu-id="1a699-109">[Implementing a Delivery Extension](implementing-a-delivery-extension.md) </span></span>  
 [<span data-ttu-id="1a699-110">Reporting Services 확장 라이브러리</span><span class="sxs-lookup"><span data-stu-id="1a699-110">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
