---
title: 데이터베이스에 대한 액세스 권한 부여 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ''
ms.topic: conceptual
helpviewer_keywords:
- database access
ms.assetid: 686edfe2-3650-48a6-a2da-9d46fa211ad8
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: 45b6d6c8dcd9c04d18489807271802aafee785b9
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660246"
---
# <a name="granting-access-to-a-database"></a><span data-ttu-id="6031e-102">데이터베이스에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="6031e-102">Granting Access to a Database</span></span>
  <span data-ttu-id="6031e-103">현재 Mary는 이 인스턴스의 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]에 액세스할 수 있지만 데이터베이스에 액세스할 수 있는 권한은 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6031e-103">Mary now has access to this instance of [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], but does not have permission to access the databases.</span></span> <span data-ttu-id="6031e-104">Mary에게 데이터베이스 사용자의 권한을 부여할 때까지 Mary는 자신의 기본 데이터베이스인 **TestData** 에도 액세스할 수 없습니다.</span><span class="sxs-lookup"><span data-stu-id="6031e-104">She does not even have access to her default database **TestData** until you authorize her as a database user.</span></span>  
  
 <span data-ttu-id="6031e-105">Mary에게 액세스 권한을 부여하려면 **TestData** 데이터베이스로 전환한 다음 CREATE USER 문을 사용하여 Mary의 로그인을 Mary라는 사용자에게 매핑합니다.</span><span class="sxs-lookup"><span data-stu-id="6031e-105">To grant Mary access, switch to the **TestData** database, and then use the CREATE USER statement to map her login to a user named Mary.</span></span>  
  
### <a name="to-create-a-user-in-a-database"></a><span data-ttu-id="6031e-106">데이터베이스에서 사용자를 만들려면</span><span class="sxs-lookup"><span data-stu-id="6031e-106">To create a user in a database</span></span>  
  
1.  <span data-ttu-id="6031e-107">다음 문을 입력하고 실행하여( `computer_name` 을 컴퓨터의 이름으로 바꿈) `Mary` 데이터베이스에 대한 액세스 권한을 `TestData` 에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="6031e-107">Type and execute the following statements (replacing `computer_name` with the name of your computer) to grant `Mary` access to the `TestData` database.</span></span>  
  
    ```  
    USE [TestData];  
    GO  
  
    CREATE USER [Mary] FOR LOGIN [computer_name\Mary];  
    GO  
  
    ```  
  
     <span data-ttu-id="6031e-108">이제 Mary는 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 및 `TestData` 데이터베이스에 대한 액세스 권한을 가집니다.</span><span class="sxs-lookup"><span data-stu-id="6031e-108">Now, Mary has access to both [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] and the `TestData` database.</span></span>  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="6031e-109">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="6031e-109">Next Task in Lesson</span></span>  
 [<span data-ttu-id="6031e-110">뷰 및 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="6031e-110">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
  
