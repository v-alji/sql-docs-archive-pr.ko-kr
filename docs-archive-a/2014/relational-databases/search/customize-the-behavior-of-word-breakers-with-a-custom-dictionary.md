---
title: 사용자 지정 사전을 사용하여 단어 분리기의 동작 사용자 지정 | Microsoft 문서
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
ms.assetid: a8e278d1-aeaa-48f1-a0c6-5de232c983e4
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 9fb02a47da20134925d9b2486ea0c08091af4aa6
ms.sourcegitcommit: ad4d92dce894592a259721a1571b1d8736abacdb
ms.translationtype: MT
ms.contentlocale: ko-KR
ms.lasthandoff: 08/04/2020
ms.locfileid: "87732532"
---
# <a name="customize-the-behavior-of-word-breakers-with-a-custom-dictionary"></a><span data-ttu-id="02193-102">사용자 지정 사전을 사용하여 단어 분리기의 동작 사용자 지정</span><span class="sxs-lookup"><span data-stu-id="02193-102">Customize the Behavior of Word Breakers with a Custom Dictionary</span></span>
  <span data-ttu-id="02193-103">언어별 사용자 지정 사전 파일을 만들어 특정 언어에 대한 단어 분리기 동작을 사용자 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02193-103">You can customize the behavior of the word breaker for a particular language by creating a language-specific custom dictionary file.</span></span> <span data-ttu-id="02193-104">예를 들어 단어 분리기에서 특정 용어 또는 패턴을 분리하지 못하도록 차단할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="02193-104">For example, you can prevent the word breaker from breaking certain terms or patterns.</span></span>  
  
 <span data-ttu-id="02193-105">자세한 내용은 다음 SharePoint 문서를 참조하십시오.</span><span class="sxs-lookup"><span data-stu-id="02193-105">For more information, see the following SharePoint article:</span></span>  
  
 [<span data-ttu-id="02193-106">사용자 지정 사전 만들기(SharePoint Server 2010)</span><span class="sxs-lookup"><span data-stu-id="02193-106">Create a custom dictionary (SharePoint Server 2010)</span></span>](https://go.microsoft.com/fwlink/?LinkId=215011)  
  
 <span data-ttu-id="02193-107">[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]에서는 사용자 지정 사전 파일을 다음 폴더에 배치합니다.</span><span class="sxs-lookup"><span data-stu-id="02193-107">For [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], place custom dictionary files in the following folder:</span></span>  
  
 `C:\Program Files\Microsoft SQL Server\<instance name>\MSSQL\Binn`  
  
 <span data-ttu-id="02193-108">사용자 지정 사전 파일을 만들거나 변경한 후 다음 명령을 사용하여 SQL 전체 텍스트 데몬 시작 관리자를 다시 시작합니다.</span><span class="sxs-lookup"><span data-stu-id="02193-108">After creating or changing custom dictionary files, restart the SQL Full-text Daemon Launcher with the following command:</span></span>  
  
 `exec sp_fulltext_service 'restart_all_fdhosts'`  
  
  
