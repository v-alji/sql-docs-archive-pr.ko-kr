---
title: 개발, 테스트 및 프로덕션 데이터베이스 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- production databases [SQL Server]
- testing databases
- database testing [SQL Server]
ms.assetid: cb403330-8cbe-41c6-bd23-bc432d50f173
author: stevestein
ms.author: sstein
ms.openlocfilehash: 98ac88aec42b53012e0f57233a089bddbd3c8cae
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87730007"
---
# <a name="development-test-and-production-databases-visual-database-tools"></a><span data-ttu-id="800e9-102">개발, 테스트 및 프로덕션 데이터베이스(Visual Database Tools)</span><span class="sxs-lookup"><span data-stu-id="800e9-102">Development, Test, and Production Databases (Visual Database Tools)</span></span>
  <span data-ttu-id="800e9-103">동일한 구조의 데이터베이스가 두 개 있으면 한 데이터베이스에서 변경한 내용을 다른 데이터베이스로 전파할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="800e9-103">If you have two databases with identical structure, you can make changes in one database and propagate those changes to the other.</span></span> <span data-ttu-id="800e9-104">예를 들어, 개인 개발 데이터베이스와 그룹 범위의 테스트 데이터베이스가 있는 경우 개발 데이터베이스를 수정한 다음 해당 수정 내용을 테스트 데이터베이스로 전파할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="800e9-104">For example, if you have a personal development database and a group-wide test database, you can modify the development database, then propagate those changes to the test database.</span></span>  
  
 <span data-ttu-id="800e9-105">이를 위해서는 개발 데이터베이스를 사용하여 단일 세션에서 모든 수정 작업을 수행하고 해당 세션에 대한 변경 스크립트를 만든 다음 테스트 데이터베이스에 대해 이 스크립트를 실행해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="800e9-105">To accomplish this, perform all the modifications in a single session with the development database, create a Change Script of your session and later run the script on the test database.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="800e9-106">참고 항목</span><span class="sxs-lookup"><span data-stu-id="800e9-106">See Also</span></span>  
 [<span data-ttu-id="800e9-107">다중 사용자 환경&#40;Visual Database Tools&#41;</span><span class="sxs-lookup"><span data-stu-id="800e9-107">Multiuser Environments &#40;Visual Database Tools&#41;</span></span>](visual-database-tools.md)  
  
  
