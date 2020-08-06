---
title: 원본 데이터베이스 파일 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transferdatabasetask.sourcedbfiles.f1
ms.assetid: 7dc6bfeb-37c1-45e8-a705-a87564922265
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 31f0c0e0c633ead0c093bdc8e1f20c9b8f23cc28
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87742343"
---
# <a name="source-database-files"></a><span data-ttu-id="ad8f7-102">원본 데이터베이스 파일</span><span class="sxs-lookup"><span data-stu-id="ad8f7-102">Source database files</span></span>
  <span data-ttu-id="ad8f7-103">**원본 데이터베이스 파일** 대화 상자를 사용하여 원본 서버의 데이터베이스 파일 이름 및 위치를 보거나 데이터베이스 전송 태스크에 대한 네트워크 파일 공유 위치를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-103">Use the **Source Database Files** dialog box to view the database file names and locations on the source server, or to specify a network file share location for the Transfer Database task.</span></span> <span data-ttu-id="ad8f7-104">이 태스크에 대한 자세한 내용은 [데이터베이스 전송 태스크](control-flow/transfer-database-task.md)를 참조하세요.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-104">For more information about this task, see [Transfer Database Task](control-flow/transfer-database-task.md).</span></span>  
  
 <span data-ttu-id="ad8f7-105">이 대화 상자를 원본 서버의 데이터베이스 파일 이름 및 위치로 채우려면 먼저 **데이터베이스 전송 태스크 편집기** 대화 상자의 **데이터베이스** 페이지에서 **SourceConnection** 및 **SourceDatabaseName** 을 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-105">To populate this dialog box with the database file names and locations on the source server, specify the **SourceConnection** and **SourceDatabaseName** first in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
## <a name="options"></a><span data-ttu-id="ad8f7-106">옵션</span><span class="sxs-lookup"><span data-stu-id="ad8f7-106">Options</span></span>  
 <span data-ttu-id="ad8f7-107">**원본 파일**</span><span class="sxs-lookup"><span data-stu-id="ad8f7-107">**Source File**</span></span>  
 <span data-ttu-id="ad8f7-108">전송할 원본 서버의 데이터베이스 파일 이름입니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-108">Database file names on the source server that will be transferred.</span></span> <span data-ttu-id="ad8f7-109">**원본 파일** 은 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-109">**Source File** is read only.</span></span>  
  
 <span data-ttu-id="ad8f7-110">**원본 폴더**</span><span class="sxs-lookup"><span data-stu-id="ad8f7-110">**Source Folder**</span></span>  
 <span data-ttu-id="ad8f7-111">전송할 데이터베이스 파일이 있는 원본 서버의 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-111">Folder on the source server where the database files to be transferred reside.</span></span> <span data-ttu-id="ad8f7-112">**원본 폴더** 는 읽기 전용입니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-112">**Source Folder** is read only.</span></span>  
  
 <span data-ttu-id="ad8f7-113">**네트워크 파일 공유**</span><span class="sxs-lookup"><span data-stu-id="ad8f7-113">**Network File Share**</span></span>  
 <span data-ttu-id="ad8f7-114">데이터베이스 파일을 전송할 원본 서버의 네트워크 공유 폴더입니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-114">Network shared folder on the source server from where the database files will be transferred.</span></span> <span data-ttu-id="ad8f7-115">오프라인 모드에서 데이터베이스를 전송할 때는 **데이터베이스 전송 태스크 편집기** 대화 상자의 **데이터베이스** 페이지에서 **Method** 에 대해 **DatabaseOffline** 을 지정하여 **네트워크 파일 공유** 를 사용합니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-115">Use **Network File Share** when you transfer a database in offline mode by specifying **DatabaseOffline** for **Method** in the **Databases** page of the **Transfer Database Task Editor** dialog box.</span></span>  
  
 <span data-ttu-id="ad8f7-116">네트워크 파일 공유 위치를 입력하거나 찾아보기 단추 **(...)** 를 클릭하여 네트워크 파일 공유 위치를 찾습니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-116">Enter the network file share location, or click the browse button **(...)** to locate the network file share location.</span></span>  
  
 <span data-ttu-id="ad8f7-117">오프라인 모드에서 데이터베이스를 전송할 때는 데이터베이스 파일이 대상 서버에 전송되기 전에 원본 서버의 **네트워크 파일 공유** 위치에 복사됩니다.</span><span class="sxs-lookup"><span data-stu-id="ad8f7-117">When you transfer a database in offline mode, the database files are copied to the **Network file share** location on the source server before they are transferred to the destination server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad8f7-118">참고 항목</span><span class="sxs-lookup"><span data-stu-id="ad8f7-118">See Also</span></span>  
 <span data-ttu-id="ad8f7-119">[Integration Services 오류 및 메시지 참조](../../2014/integration-services/integration-services-error-and-message-reference.md) </span><span class="sxs-lookup"><span data-stu-id="ad8f7-119">[Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md) </span></span>  
 <span data-ttu-id="ad8f7-120">[데이터베이스 전송 태스크 편집기 &#40;일반 페이지&#41;](general-page-of-integration-services-designers-options.md) </span><span class="sxs-lookup"><span data-stu-id="ad8f7-120">[Transfer Database Task Editor &#40;General Page&#41;](general-page-of-integration-services-designers-options.md) </span></span>  
 [<span data-ttu-id="ad8f7-121">데이터베이스 전송 태스크 편집기&#40;데이터베이스 페이지&#41;</span><span class="sxs-lookup"><span data-stu-id="ad8f7-121">Transfer Database Task Editor &#40;Databases Page&#41;</span></span>](../../2014/integration-services/transfer-database-task-editor-databases-page.md)  
  
  
