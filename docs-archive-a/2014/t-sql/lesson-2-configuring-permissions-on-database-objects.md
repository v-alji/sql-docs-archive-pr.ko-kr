---
title: '2단원: 데이터베이스 개체에 대한 사용 권한 구성 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: t-sql
ms.topic: conceptual
helpviewer_keywords:
- database permissions
ms.assetid: f964b66a-ec32-44c2-a185-6a0f173bfa22
author: VanMSFT
ms.author: vanto
ms.openlocfilehash: fcc6ee3ddf9be072b51bd568fd3e72eb6c871785
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87740652"
---
# <a name="lesson-2-configuring-permissions-on-database-objects"></a><span data-ttu-id="afbd1-102">2단원: 데이터베이스 개체에 대한 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="afbd1-102">Lesson 2: Configuring Permissions on Database Objects</span></span>
  <span data-ttu-id="afbd1-103">데이터베이스에 대한 액세스 권한을 사용자에게 부여하는 작업은 3개의 단계로 구성됩니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-103">Granting a user access to a database involves three steps.</span></span> <span data-ttu-id="afbd1-104">먼저 로그인을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-104">First, you create a login.</span></span> <span data-ttu-id="afbd1-105">로그인을 사용하여 사용자는 [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)]에 연결할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-105">The login lets the user connect to the [!INCLUDE[ssDEnoversion](../includes/ssdenoversion-md.md)].</span></span> <span data-ttu-id="afbd1-106">그런 다음 지정된 데이터베이스에서 로그인을 사용자로 구성합니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-106">Then you configure the login as a user in the specified database.</span></span> <span data-ttu-id="afbd1-107">마지막으로 데이터베이스 개체에 대한 사용 권한을 사용자에게 부여합니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-107">And finally, you grant that user permission to database objects.</span></span> <span data-ttu-id="afbd1-108">이 단원에서는 이러한 3개의 단계와 뷰 및 저장 프로시저를 개체로 만드는 방법을 보여 줍니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-108">This lesson shows you these three steps, and shows you how to create a view and a stored procedure as the object.</span></span>  
  
 <span data-ttu-id="afbd1-109">이 단원에서는 다음 항목을 다룹니다.</span><span class="sxs-lookup"><span data-stu-id="afbd1-109">This lesson contains the following topics:</span></span>  
  
-   [<span data-ttu-id="afbd1-110">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="afbd1-110">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
-   [<span data-ttu-id="afbd1-111">데이터베이스에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="afbd1-111">Granting Access to a Database</span></span>](lesson-2-2-granting-access-to-a-database.md)  
  
-   [<span data-ttu-id="afbd1-112">뷰 및 저장 프로시저 만들기</span><span class="sxs-lookup"><span data-stu-id="afbd1-112">Creating Views and Stored Procedures</span></span>](lesson-2-3-creating-views-and-stored-procedures.md)  
  
-   [<span data-ttu-id="afbd1-113">데이터베이스 개체에 대한 액세스 권한 부여</span><span class="sxs-lookup"><span data-stu-id="afbd1-113">Granting Access to a Database Object</span></span>](lesson-2-4-granting-access-to-a-database-object.md)  
  
-   [<span data-ttu-id="afbd1-114">요약: 데이터베이스 개체에 대한 사용 권한 구성</span><span class="sxs-lookup"><span data-stu-id="afbd1-114">Summary: Configuring Permissions on Database Objects</span></span>](lesson-2-5-summary-configuring-permissions-on-database-objects.md)  
  
## <a name="next-task-in-lesson"></a><span data-ttu-id="afbd1-115">단원의 다음 태스크</span><span class="sxs-lookup"><span data-stu-id="afbd1-115">Next Task in Lesson</span></span>  
 [<span data-ttu-id="afbd1-116">로그인 만들기</span><span class="sxs-lookup"><span data-stu-id="afbd1-116">Creating a Login</span></span>](lesson-2-1-creating-a-login.md)  
  
  
