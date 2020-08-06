---
title: 원격 서버에서 부하가 분산 된 패키지에 대 한 로깅 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- logs [Integration Services], remote packages
ms.assetid: fd571567-b625-4f9a-8b7e-42c5c588b11b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: b45fa6607d6edc1559d8ebcbbbc7598e11eac408
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87651103"
---
# <a name="logging-for-load-balanced-packages-on-remote-servers"></a><span data-ttu-id="9b225-102">원격 서버의 로드 균형 조정된 패키지 로깅</span><span class="sxs-lookup"><span data-stu-id="9b225-102">Logging for Load Balanced Packages on Remote Servers</span></span>
  <span data-ttu-id="9b225-103">모든 자식 패키지가 동일한 로그 공급자를 사용하고 동일한 대상에 쓰는 경우 관리자가 보다 쉽게 여러 서버에서 실행되는 모든 자식 패키지에 대한 로그를 관리할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b225-103">It is easier for an administrator to manage the logs for all the child packages that are running on various servers when all the child packages use the same log provider and they all write to the same destination.</span></span> <span data-ttu-id="9b225-104">모든 자식 패키지에 공통된 로그 파일을 만드는 한 가지 방법은 SQL Server 로그 공급자에 이벤트를 기록하도록 자식 패키지를 구성하는 것입니다.</span><span class="sxs-lookup"><span data-stu-id="9b225-104">One way that you can create a common log file for all child packages is to configure the child packages to log their events to a SQL Server log provider.</span></span> <span data-ttu-id="9b225-105">모든 패키지가 동일한 데이터베이스, 동일한 서버 및 서버의 동일한 인스턴스를 사용하도록 구성할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b225-105">You can configure all the packages to use the same database, the same server, and the same instance of the server.</span></span>  
  
 <span data-ttu-id="9b225-106">관리자는 단일 서버에 로그온하여 모든 자식 패키지에 대한 로그 파일을 볼 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="9b225-106">To view the log files, the administrator only has to log on to a single server to view the log files for all child packages.</span></span>  
  
## <a name="related-tasks"></a><span data-ttu-id="9b225-107">관련 작업</span><span class="sxs-lookup"><span data-stu-id="9b225-107">Related Tasks</span></span>  
 <span data-ttu-id="9b225-108">패키지에서 로깅을 사용하도록 설정하는 방법은 [SQL Server Data Tools에서 패키지 로깅 설정](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md)을 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="9b225-108">For information about how to enable logging in a package, see [Enable Package Logging in SQL Server Data Tools](../../2014/integration-services/enable-package-logging-in-sql-server-data-tools.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b225-109">참고 항목</span><span class="sxs-lookup"><span data-stu-id="9b225-109">See Also</span></span>  
 [<span data-ttu-id="9b225-110">Integration Services&#40;SSIS&#41; 로깅</span><span class="sxs-lookup"><span data-stu-id="9b225-110">Integration Services &#40;SSIS&#41; Logging</span></span>](performance/integration-services-ssis-logging.md)  
  
  
