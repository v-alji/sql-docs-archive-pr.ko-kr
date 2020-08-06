---
title: 데이터 처리 확장 프로그램 제거 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services
ms.topic: reference
helpviewer_keywords:
- deleting data processing extensions
- data processing extensions [Reporting Services], removing
- removing data processing extensions
ms.assetid: 1d89e32b-0631-44f6-8178-a57fb791d26d
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9f5dfd3a6a7615fa3fd91c917bba6dbf0808f0f9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87741584"
---
# <a name="removing-a-data-processing-extension"></a><span data-ttu-id="31aac-102">데이터 처리 확장 프로그램 제거</span><span class="sxs-lookup"><span data-stu-id="31aac-102">Removing a Data Processing Extension</span></span>
  <span data-ttu-id="31aac-103">데이터 처리 확장 프로그램을 제거하려면 구성 파일에서 데이터 처리 확장 프로그램에 대한 **Extension** 요소를 제거하면 됩니다.</span><span class="sxs-lookup"><span data-stu-id="31aac-103">To remove a data processing extension, simply remove the **Extension** element for your data processing extension from the configuration file.</span></span> <span data-ttu-id="31aac-104">보고서 서버 및 보고서 디자이너에 대한 항목을 만든 경우에는 RSReportServer.config 파일과 RSReportDesigner.config 파일 모두에서 **Extension** 요소를 제거합니다.</span><span class="sxs-lookup"><span data-stu-id="31aac-104">If you made entries for a report server as well as Report Designer, remove the **Extension** element from both the RSReportServer.config and RSReportDesigner.config files.</span></span> <span data-ttu-id="31aac-105">구성 정보를 제거한 후에는 구성 요소에서 데이터 처리 확장 프로그램을 사용할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="31aac-105">After the configuration information is removed, the data processing extension is no longer available to the component.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="31aac-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="31aac-106">See Also</span></span>  
 <span data-ttu-id="31aac-107">[Reporting Services 확장](../reporting-services-extensions.md) </span><span class="sxs-lookup"><span data-stu-id="31aac-107">[Reporting Services Extensions](../reporting-services-extensions.md) </span></span>  
 <span data-ttu-id="31aac-108">[데이터 처리 확장 프로그램 구현](implementing-a-data-processing-extension.md) </span><span class="sxs-lookup"><span data-stu-id="31aac-108">[Implementing a Data Processing Extension](implementing-a-data-processing-extension.md) </span></span>  
 [<span data-ttu-id="31aac-109">Reporting Services 확장 프로그램 라이브러리</span><span class="sxs-lookup"><span data-stu-id="31aac-109">Reporting Services Extension Library</span></span>](../reporting-services-extension-library.md)  
  
  
