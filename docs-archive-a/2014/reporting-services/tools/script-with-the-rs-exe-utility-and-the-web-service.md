---
title: rs.exe 유틸리티 및 웹 서비스를 사용한 스크립트 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- Web service [Reporting Services], scripts
- rs utility
- XML Web service [Reporting Services], scripts
- Report Server Web service, scripts
- scripts [Reporting Services], Web service
ms.assetid: 0ec5ac6e-b3cf-49cd-96f6-6b4b7dc29982
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 9d84bb8722fd31a08ff7788ad31c601b377c23d6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652014"
---
# <a name="script-with-the-rsexe-utility-and-the-web-service"></a><span data-ttu-id="9bb36-102">rs.exe 유틸리티 및 웹 서비스를 사용한 스크립팅</span><span class="sxs-lookup"><span data-stu-id="9bb36-102">Script with the rs.exe Utility and the Web Service</span></span>
  <span data-ttu-id="9bb36-103">개발자와 보고서 서버 관리자는 **rs** 유틸리티(RS.exe)를 사용하여 보고서 서버 작업을 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb36-103">Developers and report server administrators can perform operations on a report server through the use of the **rs** utility (RS.exe).</span></span> <span data-ttu-id="9bb36-104">이 유틸리티를 사용하면 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)]으로 작성한 스크립트를 사용하여 보고서 서버를 프로그래밍 방식으로 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb36-104">Using this utility, you can programmatically administer a report server using scripts written with [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)].</span></span>  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] <span data-ttu-id="9bb36-105">스크립트를 사용하여 모든 보고서 서버 웹 서비스 작업을 실행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb36-105">scripts can be used to run any of the Report Server Web service operations.</span></span> <span data-ttu-id="9bb36-106">서버의 여러 보고서에 보안 정보를 복사하고, 항목을 추가 및 삭제하고, 보고서 서버 항목을 다른 서버로 복사하는 등에 스크립팅 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9bb36-106">Scripting can be used to copy security to multiple reports on a server, to add and delete items, to copy report server items from one server to another and more.</span></span> <span data-ttu-id="9bb36-107">스크립팅 환경에 대한 자세한 내용은 [Reporting Services 스크립트 파일 실행](run-a-reporting-services-script-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bb36-107">For more information about the scripting environment, see [Run a Reporting Services Script File](run-a-reporting-services-script-file.md).</span></span> <span data-ttu-id="9bb36-108">스크립트 파일은 특정 형식을 사용하며 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET으로 작성합니다.</span><span class="sxs-lookup"><span data-stu-id="9bb36-108">Script files take a certain format and are written in [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] .NET.</span></span> <span data-ttu-id="9bb36-109">자세한 내용은 [Reporting Services 스크립트 파일 형식 지정](format-a-reporting-services-script-file.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9bb36-109">For more information, see [Format a Reporting Services Script File](format-a-reporting-services-script-file.md).</span></span>  
  
 <span data-ttu-id="9bb36-110">스크립트 예제는 다음을 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="9bb36-110">For script samples, see the following:</span></span>  
  
 <span data-ttu-id="9bb36-111">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md)입니다.</span><span class="sxs-lookup"><span data-stu-id="9bb36-111">[Sample Reporting Services rs.exe Script to Migrate Content between Report Servers](sample-reporting-services-rs-exe-script-to-copy-content-between-report-servers.md).</span></span>  
  
 <span data-ttu-id="9bb36-112">[SQL Server Reporting Services 제품 예제](https://go.microsoft.com/fwlink/?LinkId=177889).</span><span class="sxs-lookup"><span data-stu-id="9bb36-112">[SQL Server Reporting Services Product Samples](https://go.microsoft.com/fwlink/?LinkId=177889).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bb36-113">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9bb36-113">See Also</span></span>  
 <span data-ttu-id="9bb36-114">[배포 및 관리 태스크 스크립팅](script-deployment-and-administrative-tasks.md) </span><span class="sxs-lookup"><span data-stu-id="9bb36-114">[Script Deployment and Administrative Tasks](script-deployment-and-administrative-tasks.md) </span></span>  
 <span data-ttu-id="9bb36-115">[보고서 서버 웹 서비스](../report-server-web-service/report-server-web-service.md) </span><span class="sxs-lookup"><span data-stu-id="9bb36-115">[Report Server Web Service](../report-server-web-service/report-server-web-service.md) </span></span>  
 <span data-ttu-id="9bb36-116">[기술 참조&#40;SSRS&#41;](../technical-reference-ssrs.md) </span><span class="sxs-lookup"><span data-stu-id="9bb36-116">[Technical Reference &#40;SSRS&#41;](../technical-reference-ssrs.md) </span></span>  
 [<span data-ttu-id="9bb36-117">RS.exe 유틸리티&#40;SSRS&#41;</span><span class="sxs-lookup"><span data-stu-id="9bb36-117">RS.exe Utility &#40;SSRS&#41;</span></span>](rs-exe-utility-ssrs.md)  
  
  
