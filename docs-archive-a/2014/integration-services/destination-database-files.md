---
title: 대상 데이터베이스 파일 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.destdbfiles.f1
ms.assetid: f6f90417-86fb-4b8c-a790-0b215c344ef6
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 0d0ab2c0ff39fc728afc17b59f0d4bae076e4022
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87660074"
---
# <a name="destination-database-files"></a><span data-ttu-id="54629-102">대상 데이터베이스 파일</span><span class="sxs-lookup"><span data-stu-id="54629-102">Destination Database Files</span></span>
  <span data-ttu-id="54629-103">**대상 데이터베이스 파일** 대화 상자를 사용하여 대상 서버의 데이터베이스 파일 이름 및 위치를 확인 또는 변경하거나 데이터베이스 전송 태스크에 대한 네트워크 파일 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="54629-103">Use the **Destination Database Files** dialog box to view or change the database file names and locations on the destination server, or to specify a network file location for the Transfer Database task.</span></span> <span data-ttu-id="54629-104">이 태스크에 대한 자세한 내용은 [데이터베이스 전송 태스크](control-flow/transfer-database-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="54629-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="54629-105">이 대화 상자를 원본 서버의 데이터베이스 파일 이름 및 위치로 자동으로 채우려면 먼저 **데이터베이스 전송 태스크 편집기**대화 상자의 **데이터베이스**페이지에서 **SourceConnection** , **SourceDatabaseName** 및 **SourceDatabaseFiles** 를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="54629-105">To automatically populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection**, **SourceDatabaseName**, and **SourceDatabaseFiles** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="54629-106">옵션</span><span class="sxs-lookup"><span data-stu-id="54629-106">Options</span></span>  
 <span data-ttu-id="54629-107">**대상 파일**</span><span class="sxs-lookup"><span data-stu-id="54629-107">**Destination File**</span></span>  
 <span data-ttu-id="54629-108">전송된 대상 서버의 데이터베이스 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="54629-108">Names of the transferred database files on the destination server.</span></span>  
  
 <span data-ttu-id="54629-109">파일 이름을 입력하거나 파일 이름을 클릭하여 편집합니다.</span><span class="sxs-lookup"><span data-stu-id="54629-109">Enter the file name, or click the file name to edit it.</span></span>  
  
 <span data-ttu-id="54629-110">**대상 폴더**</span><span class="sxs-lookup"><span data-stu-id="54629-110">**Destination Folder**</span></span>  
 <span data-ttu-id="54629-111">데이터베이스 파일을 전송할 대상 서버의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="54629-111">Folder on the destination server where the database files will be transferred to.</span></span>  
  
 <span data-ttu-id="54629-112">폴더 경로를 입력하거나, 폴더 경로를 클릭하여 편집하거나, 찾아보기를 클릭하여 대상 서버의 데이터베이스 파일을 전송할 폴더를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="54629-112">Enter the folder path, click the folder path to edit it, or click browse to locate the folder where you want to transfer the database files on the destination server.</span></span>  
  
 <span data-ttu-id="54629-113">**네트워크 파일 공유**</span><span class="sxs-lookup"><span data-stu-id="54629-113">**Network File Share**</span></span>  
 <span data-ttu-id="54629-114">데이터베이스 파일을 전송할 대상 서버의 네트워크 공유 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="54629-114">Network shared folder on the destination server where the database files will be transferred to.</span></span> <span data-ttu-id="54629-115">오프라인 모드에서 데이터베이스를 전송할 때는 **데이터베이스 전송 태스크 편집기** 대화 상자의 **데이터베이스** 페이지에서 **Method** 에 대해 **DatabaseOffline** 을 지정하여 **네트워크 파일 공유** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="54629-115">Use **Network file share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="54629-116">네트워크 파일 공유 위치를 입력하거나 찾아보기를 클릭하여 네트워크 파일 공유 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="54629-116">Enter the network file share location, or click browse to locate the network file share location.</span></span>  
  
 <span data-ttu-id="54629-117">오프라인 모드에서 데이터베이스를 전송할 때는 데이터베이스 파일이 **대상 폴더** 위치에 전송되기 전에 **네트워크 파일 공유** 위치에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="54629-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location before they are transferred to the **Destination folder** location.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54629-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="54629-118">See Also</span></span>  
 <span data-ttu-id="54629-119">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="54629-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="54629-120">[데이터베이스 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="54629-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="54629-121">데이터베이스 전송 태스크 편집기&#40;데이터베이스 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="54629-121">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
