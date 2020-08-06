---
title: 기업 내의 자동화된 관리 튜닝 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- performance [SQL Server], automated administration
- tuning automated administration [SQL Server]
- monitoring performance [SQL Server], automated administration
ms.assetid: 671fed35-3859-4b0d-8f38-4dd07436857e
author: stevestein
ms.author: sstein
ms.openlocfilehash: 52fef95cd13beafef89701196a445a90e6fc1eb2
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87652528"
---
# <a name="tune-automated-administration-across-an-enterprise"></a><span data-ttu-id="15e04-102">기업 내의 자동화된 관리 튜닝</span><span class="sxs-lookup"><span data-stu-id="15e04-102">Tune Automated Administration Across an Enterprise</span></span>
  <span data-ttu-id="15e04-103">Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 에이전트를 통해 다중 서버를 관리할 때 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]의 자체 튜닝 기능을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15e04-103">Multiserver administration with Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent takes advantage of the self-tuning features of [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].</span></span> <span data-ttu-id="15e04-104">따라서 정상 조건에서 추가 작업 튜닝은 필요하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="15e04-104">Therefore, under normal conditions, additional job tuning is not necessary.</span></span> <span data-ttu-id="15e04-105">그러나 작업을 실행하고 경고를 생성하고 운영자에게 알릴 때 네트워크 로드가 증가됩니다.</span><span class="sxs-lookup"><span data-stu-id="15e04-105">However, network loads increase when you run jobs, generate alerts, and notify operators.</span></span> <span data-ttu-id="15e04-106">기업 내에서 자동화된 관리를 튜닝하여 이러한 작업으로 인한 네트워크 트래픽을 최소화할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="15e04-106">You can tune automated administration across an enterprise to minimize the network traffic these activities cause.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15e04-107">참고 항목</span><span class="sxs-lookup"><span data-stu-id="15e04-107">See Also</span></span>  
 [<span data-ttu-id="15e04-108">성능 카운터</span><span class="sxs-lookup"><span data-stu-id="15e04-108">Performance Counters</span></span>](../../integration-services/performance/performance-counters.md)  
  
  
